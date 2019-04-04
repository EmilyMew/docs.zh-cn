---
title: 使用 HttpClientFactory 实现复原 HTTP 请求
description: 了解如何使用自 .NET Core 2.1 起可用的 HttpClientFactory 来创建 `HttpClient` 实例，使其更轻松地在应用程序中使用。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: a55181e787b5c94e13d3945a5d97a12fed61e927
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465927"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>使用 HttpClientFactory 实现复原 HTTP 请求

自 .NET Core 2.1 起可用的 `HttpClientFactory` 是一个“固执的”工厂，用于创建在应用程序中使用的 <xref:System.Net.Http.HttpClient> 实例。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 中提供的原始 HttpClient 类的相关问题

常见的原始 [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) 类非常易于使用，但在某些情况下，许多开发人员却并未正确使用该类。 

第一个问题，当此类可释放时，将其用于 `using` 语句并不是最佳选择，因为即使释放 `HttpClient` 对象，基础套接字也不会立即释放，并可能导致严重问题：“套接字耗尽”。 有关此问题的详细信息，请参阅[你正在以错误方式使用 HttpClient，这将导致软件受损](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)博客文章。

因此，`HttpClient` 应进行一次实例化并在应用程序的生命周期中重复使用。 在负载较重的情况下，实例化每个请求的 `HttpClient` 类将耗尽可用的套接字数。 该问题会导致 `SocketException` 错误。 要解决此问题，可能的方法是将 `HttpClient` 对象创建为单一对象或静态对象，请参阅[关于 HttpClient 用法的 Microsoft 文章](/dotnet/csharp/tutorials/console-webapiclient)中的说明。 

但将 `HttpClient` 对象用作单一对象或静态对象时还有一个问题。 在这种情况下，单一或静态 `HttpClient` 不考虑 DNS 更改，请参阅 [.NET Core GitHub 存储库的问题](https://github.com/dotnet/corefx/issues/11224)一文的说明。 

为解决上述问题并使 `HttpClient` 实例管理更轻松，.NET Core 2.1 引入了新的 `HttpClientFactory`，后者可与 Polly 集成来实现弹性 HTTP 调用。   

## <a name="what-is-httpclientfactory"></a>什么是 HttpClientFactory

`HttpClientFactory` 用于：

- 提供一个中心位置，用于命名和配置逻辑 HttpClient。 例如，可以配置预配置的客户端（服务代理）以访问特定微服务。
- 通过后列方式整理出站中间件的概念：在 `HttpClient` 中委托处理程序并实现基于 Polly 的中间件以利用 Polly 的复原策略。
- `HttpClient` 已经具有委托处理程序的概念，这些委托处理程序可以链接在一起，处理出站 HTTP 请求。 将 http 客户端注册到工厂后，可使用一个允许将 Polly 策略用于重试、断路器等的 Polly 处理程序。
- 管理 HttpClientMessageHandlers 的生存期，以避免在自己管理 `HttpClient` 生存期时出现上述问题。 

## <a name="multiple-ways-to-use-httpclientfactory"></a>HttpClientFactory 的多种用法

可以通过多种方法在应用程序中使用 `HttpClientFactory`：

- 直接使用 `HttpClientFactory`
- 使用命名客户端
- 使用类型化客户端
- 使用生成的客户端

为简便起见，本指南介绍最具条理和组织性的 `HttpClientFactory` 用法，此方法就是使用类型化客户端（服务代理模式），但此[关于 HttpClientFactory 用法的文章](/aspnet/core/fundamentals/http-requests?#consumption-patterns)中当前记录并列出了全部可用的方法。  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>如何结合使用类型化客户端和 HttpClientFactory

那么，什么是“类型化客户端”？ 它只是 `DefaultHttpClientFactory` 注入时配置的 `HttpClient`。

下图显示了如何将类型化客户端与 `HttpClientFactory` 结合使用：

![ClientService（由控制器或客户端代码使用）使用由注册的 IHttpClientFactory 创建的 HttpClient。 此工厂从它管理的池中向 HttpClient 分配一个 HttpMessageHandler。 当使用扩展方法 AddHttpClient 在 DI 容器中注册 IHttpClientFactory 时，可以使用 Polly 策略配置 HttpClient。](./media/image3.5.png)

**图 8-4**。 将 HttpClientFactory 与类型化客户端类结合使用。

首先，在应用程序中设置 `HttpClientFactory`，添加对包含 `IServiceCollection` 的 `AddHttpClient()` 扩展方法的 `Microsoft.Extensions.Http` 包的引用。 此扩展方法用于注册 `DefaultHttpClientFactory`，后者用作接口 `IHttpClientFactory` 的单一实例。 它定义 `HttpMessageHandlerBuilder` 的临时配置。 此消息处理程序（`HttpMessageHandler` 对象）获取自池，可供从工厂返回的 `HttpClient` 使用。

在下一个代码中，可以看到如何使用 `AddHttpClient()` 注册需要使用 `HttpClient` 的类型化客户端（服务代理）。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

正如前面代码所示，注册客户端服务将使 `DefaultClientFactory` 创建专门为每个服务配置的 `HttpClient`，我们将在下一段中对此进行解释。

只需向 `AddHttpClient()` 注册客户端服务类，注入到类中的 `HttpClient` 对象将使用注册时提供的配置和策略。 后续部分将介绍 Polly 重试或断路器等策略。

### <a name="httpclient-lifetimes"></a>HttpClient 生存期

每次从 `IHttpClientFactory` 获取 `HttpClient` 对象时，都会返回一个新实例。 但每个 `HttpClient` 使用 `IHttpClientFactory` 汇集和重用的 `HttpMessageHandler`，以减少资源消耗，只要 `HttpMessageHandler` 的生存期尚未过期。

由于每个处理程序通常都管理自己的基础 HTTP 连接，所以有必要汇集处理程序；创建的处理程序数量如果多于必需的数量，则可能导致连接延迟。 部分处理程序还保持连接无期限地打开，这样可以防止处理程序对 DNS 更改作出反应。

池中的 `HttpMessageHandler` 对象的生存期就是池中的 `HttpMessageHandler` 实例可重用的时间长度。 默认值为两分钟，但可基于每个类型化客户端重写此值。 要重写该值，请在创建客户端时在返回的 `IHttpClientBuilder` 上调用 `SetHandlerLifetime()`，如以下代码所示：

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

每个类型化客户端都可自行配置处理程序生存期值。 将生存期设置为 `InfiniteTimeSpan` 可禁用处理程序到期。

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>实现使用注入的和配置的 HttpClient 的类型化客户端类

在上一步中，需要定义类型化客户端类，如示例代码中的类，“BasketService”、“CatalogService”、“OrderingService”等。类型化客户端是一个类，它接受 `HttpClient` 对象（通过其构造函数注入），并用它来调用某些远程 HTTP 服务。 例如:

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

类型化客户端（示例中的 CatalogService）由 DI（依赖项注入）激活，这意味着除 HttpClient 外，它还可以接受其构造函数中的任何注册服务。

类型化客户端实际上是一个暂时对象，这意味着每次需要实例时都将创建新实例，并且它将在其每次被构造时接收一个新 `HttpClient` 实例。 但是，池中的 HttpMessageHandler 对象是由多个 Http 请求重复使用的对象。

### <a name="use-your-typed-client-classes"></a>使用类型化客户端类

最后，实现类型类并向 AddHttpClient() 注册这些类后，便可在允许使用 DI 注入的服务的任何位置使用，例如在任何 Razor 页面代码或 MVC Web 应用的任何控制器中，如 eShopOnContainers 中的以下代码所示。

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) => 
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied, 
                                               int? TypesFilterApplied, 
                                               int? page, 
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0, 
                                                            itemsPage, 
                                                            BrandFilterApplied, 
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

此时，所示代码仅执行常规 Http 请求，但后续部分将展示真正的“神奇”之处 - 只需向已注册的类型化客户端添加策略和委派处理程序，将由 `HttpClient` 完成的所有 HTTP 请求在执行时都将考虑帐户复原策略，例如使用指数退避算法实现的重试、断路器或用于实现额外安全功能（如使用身份验证令牌或任何其他自定义功能）的任何其他自定义委托处理程序。 

## <a name="additional-resources"></a>其他资源

- **在 .NET Core 中使用 HttpClientFactory**\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **HttpClientFactory GitHub 存储库**\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

>[!div class="step-by-step"]
>[上一页](explore-custom-http-call-retries-exponential-backoff.md)
>[下一页](implement-http-call-retries-exponential-backoff-polly.md)
