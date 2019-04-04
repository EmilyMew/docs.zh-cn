---
title: 通过 Polly 实现使用指数退避算法的 HTTP 调用重试
description: 了解如何使用 Polly 和 HttpClientFactory 处理 HTTP 故障。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 07333b84896c223f076e9c36cc90ab7ea7ac37c7
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465719"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a>通过 HttpClientFactory 和 Polly 策略实现使用指数退避算法的 HTTP 调用重试

建议的使用指数退避算法的重试方法是利用更高级的 .NET 库，如开放源 [Polly](https://github.com/App-vNext/Polly) 库。

Polly 是一个 .NET 库，提供恢复能力和瞬态故障处理功能。 通过应用 Polly 策略（如重试、断路器、舱壁隔离、超时和回退）即可实现这些功能。 Polly 面向 .NET 4.x 和 .NET Standard 库 1.0（支持 .NET Core）。

但是，将包含自定义代码的 Polly 库与 HttpClient 配合使用的过程非常复杂。 eShopOnContainers 的原始版本中包含基于 Polly 的 [ResilientHttpClient 构建基块](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/Resilience/Resilience.Http/ResilientHttpClient.cs)。 但随着 HttpClientFactory 的发布，复原 Http 通信变得更易于实现，因此已弃用 eShopOnContainers 中的构建基块。 

以下步骤说明如何通过集成到 HttpClientFactory 中的 Polly（已在上一部分中说明）使用 Http 重试。

**引用 ASP.NET Core 2.2 包**

自 .NET Core 2.1 起提供 `HttpClientFactory`，但建议在项目中使用 NuGet 中的最新 ASP.NET Core 2.2 包。 通常需要 `AspNetCore` 元包和扩展包 `Microsoft.Extensions.Http.Polly`。

**使用 Polly 的重试策略在 Startup 中配置客户端**

如前面部分中所示，需要在标准 Startup.ConfigureServices(...) 方法中定义已命名或类型化的客户端 HttpClient 配置，但现在，可使用指数退避算法添加用于指定 Http 重试策略的增量代码，如下所示：

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

将策略添加至将要使用的 `HttpClient` 对象需要使用 AddPolicyHandler() 方法。 在此示例中，将使用指数退避算法为 Http 重试添加 Polly 策略。

若要获得更加模块化的方法，可在 `Startup.cs` 文件内的单独方法中定义 Http 重试策略，如以下代码所示：

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

使用 Polly 可定义一个重试策略，其中包含重试次数、指数退避算法配置以及在出现 HTTP 异常时要采取的操作，例如记录错误。 在此示例中，该策略配置为尝试 6 次（采用指数重试），以 2 秒为起始值。 

也就是说，它将以 2 秒为起始值尝试 6 次，且每两次重试之间的秒数为指数关系。

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a>将抖动策略添加到重试策略

在高并发率、高可伸缩性和高争用的情况下，常规重试策略可能会对系统产生影响。 在部分运行中断的情况下，有可能会有许多客户端同时发出相似的重试操作，从而形成操作高峰，为克服这种情况，一个好办法是向重试算法或策略中添加抖动策略。 由于增加了指数退避的随机性，这可能会改进端到端系统的整体性能。 这样在出现问题时可以分散峰值。 使用普通 Polly 策略时，用于实现抖动的代码类似下面的示例：

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a>其他资源

- **重试模式**\
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- **Polly 和 HttpClientFactory**\
  [https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory](https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory)

- **Polly（.NET 复原能力和暂时性故障处理库）**\
  [https://github.com/App-vNext/Polly](https://github.com/App-vNext/Polly)

- **Marc Brooker。抖动：随机性使操作变得更好**\
  [https://brooker.co.za/blog/2015/03/21/backoff.html](https://brooker.co.za/blog/2015/03/21/backoff.html)

>[!div class="step-by-step"]
>[上一页](explore-custom-http-call-retries-exponential-backoff.md)
>[下一页](implement-circuit-breaker-pattern.md)