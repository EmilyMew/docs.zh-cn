---
title: WCF 服务和 ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 80f4f9a473f223928981ee3f0c2e9f2464cbafaf
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463470"
---
# <a name="wcf-services-and-aspnet"></a>WCF 服务和 ASP.NET

本主题讨论托管 Windows Communication Foundation (WCF) 服务的并排方案使用 ASP.NET 和在 ASP.NET 兼容模式中承载。

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>托管 WCF 的并排方案使用 ASP.NET

在 Internet 信息服务 (IIS) 承载的 WCF 服务可以是与放在一起。ASPX 页和 ASMX Web 服务在单个公共应用程序域内。 ASP.NET 提供公共基础结构服务，例如 AppDomain 管理以及针对 WCF 和 ASP.NET HTTP 运行时动态编译。 WCF 的默认配置是通过并行使用 ASP.NET。

![屏幕截图显示 WCF 服务和 ASP.NET： 共享状态。](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

ASP.NET HTTP 运行库处理 ASP.NET 请求但不参与处理的请求发送到 WCF 服务，即使这些服务承载在同一 AppDomain 中按原样 ASP.NET 内容也是如此。 相反，WCF 服务模型会截获消息发送到 WCF 服务，并将其路由通过 WCF 传输协议/通道堆栈。

并行模型的结果如下：

- ASP.NET 和 WCF 服务可以共享 AppDomain 状态。 因为这两个框架可以在同一个 AppDomain 中共存，WCF 还可以使用 ASP.NET （包括静态变量、 事件等） 中共享 AppDomain 状态。

- WCF 服务行为保持一致，独立于宿主环境和传输。 ASP.NET HTTP 运行库与 IIS/ASP.NET 宿主环境和 HTTP 通信是有意耦合在一起的。 相反，WCF 旨在跨宿主环境的行为一致 (WCF 行为的一致性同时内部和外部 IIS) 以及跨传输 (承载于 IIS 7.0 及更高版本的服务公开，所有终结点之间具有一致的行为即使一些这些终结点使用 HTTP 之外的协议。）

- 在 AppDomain 中，由 HTTP 运行时实现的功能适用于 ASP.NET 内容而不适用于 WCF。 包含 ASP.NET 内容的 AppDomain 内承载的 WCF 服务不适用于 ASP.NET 应用程序平台的许多特定于 HTTP 的功能。 这些功能的示例包括：

    - HttpContext:<xref:System.Web.HttpContext.Current%2A>始终是`null`时从 WCF 服务内部进行访问。 请改用 <xref:System.ServiceModel.Channels.RequestContext>。

    - 基于文件的授权：WCF 安全模型不允许的访问控制列表 (ACL) 确定是否授权服务请求时应用于服务的.svc 文件中。

    - 基于配置的 URL 授权：同样，WCF 安全模型不符合 System.Web 的中指定的任何基于 URL 的授权规则\<授权 > 配置元素。 如果服务驻留在受保护的 ASP 的 URL 空间，用于 WCF 请求将忽略这些设置。NET 的 URL 授权规则。

    - HttpModule 扩展性：WCF 托管基础结构截获 WCF 请求时<xref:System.Web.HttpApplication.PostAuthenticateRequest>事件引发并不会返回到 ASP.NET HTTP 管道中处理。 编码为在管道的后期截获请求的模块不截获 WCF 请求。

    - ASP.NET 模拟：默认情况下，WCF 请求总是作为运行 IIS 进程标识，即使 ASP.NET 设置来启用模拟使用 System.Web 的\<identity impersonate ="true"/ > 配置选项。

这些限制仅适用于 IIS 应用程序中承载的 WCF 服务。 存在 WCF 不会影响 ASP.NET 内容的行为。

需要由 HTTP 管道传统上提供的功能的 WCF 应用程序应考虑使用 WCF 等效项，该主机和传输协议独立：

- <xref:System.ServiceModel.OperationContext>，而不是 <xref:System.Web.HttpContext>。

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>，而不是 ASP.NET 的文件/URL 授权。

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 或自定义分层通道，而不是 HTTP 模块。

- 使用 WCF，而不 System.Web 模拟的每个操作进行模拟。

或者，可以考虑在 WCF 的 ASP.NET 兼容性模式下运行你的服务。

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>在 ASP.NET 兼容模式下的托管 WCF 服务

尽管 WCF 模型旨在跨宿主环境和传输行为一致，很多情况下应用程序不需要这种程度的灵活性。 WCF 的 ASP.NET 兼容模式是适用于方案，不需要向 IIS 之外或通过除 HTTP 之外的协议进行通信的主机功能，但使用的所有 ASP.NET Web 应用程序平台的功能。

与不同的是默认的并行配置中，其中 WCF 托管基础结构截获 WCF 消息，并将其路由到 HTTP 管道之外，在 ASP.NET 兼容模式中运行的 WCF 服务完全参与 ASP.NET HTTP 请求生命周期。 在兼容性模式下，WCF 服务使用通过 HTTP 管道<xref:System.Web.IHttpHandler>实现中，类似于方法请求处理 ASPX 页和 ASMX Web 服务。 因此，WCF 的行为相同 ASMX 以下 ASP.NET 功能方面：

- <xref:System.Web.HttpContext>：在 ASP.NET 兼容模式中运行的 WCF 服务可以访问<xref:System.Web.HttpContext.Current%2A>及其关联状态。

- 基于文件的授权：在 ASP.NET 兼容模式下运行的 WCF 服务可以通过将文件系统访问控制列表 (Acl) 附加到服务的.svc 文件安全。

- 可配置 URL 授权：ASP。在 ASP.NET 兼容模式中运行 WCF 服务时，NET 的 URL 授权规则是针对 WCF 请求强制执行。

- <xref:System.Web.HttpModuleCollection> 可扩展性：在 ASP.NET 兼容模式中运行的 WCF 服务完全参与 ASP.NET HTTP 请求生命周期，因为 HTTP 管道中配置的任何 HTTP 模块是能够对 WCF 请求之前和之后服务调用。

- ASP.NET 模拟：WCF 服务使用当前的 asp.net 标识运行模拟线程，这可能会不同于 IIS 进程标识，如果对应用程序启用 ASP.NET 模拟。 如果 ASP.NET 模拟和 WCF 模拟启用特定服务操作，服务实现最终运行使用 WCF 从获得的标识。

在通过以下配置 （位于应用程序的 Web.config 文件） 的应用程序级别启用 WCF 的 ASP.NET 兼容模式：

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

此值默认为"`true`"如果未指定。 此值设置为"`false`"指示应用程序中运行的所有 WCF 服务将在 ASP.NET 兼容模式下都运行。

无论是哪个 asp.net 的应用程序内运行单独的服务实现 ASP.NET 兼容模式暗含的本质上不同于 WCF 默认的请求处理语义，因为有控制的功能已启用兼容性模式。 服务可以使用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 来指示其是否支持 ASP.NET 兼容模式。 此特性的默认值为 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>。

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

下表演示应用程序范围的兼容模式设置如何与单独服务指定的支持级别交互：

|应用程序范围的兼容模式设置|[AspNetCompatibilityRequirementsMode]<br /><br /> 设置|观察到的结果|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|服务成功激活。|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服务成功激活。|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|服务接收消息时发生激活错误。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|服务接收消息时发生激活错误。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|服务成功激活。|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|服务成功激活。|

> [!NOTE]
> IIS 7.0 和 WAS 允许 WCF 服务通过 HTTP 之外的协议进行通信。 但是，不允许的应用程序已启用 ASP.NET 兼容模式中运行的 WCF 服务公开非 HTTP 终结点。 在服务接收其第一条消息时，这种配置会生成激活异常。

有关启用 ASP.NET 兼容模式的 WCF 服务的详细信息，请参阅<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>并[ASP.NET 兼容性](../samples/aspnet-compatibility.md)示例。

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server App Fabric 承载功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))