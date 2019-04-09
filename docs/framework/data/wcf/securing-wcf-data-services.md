---
title: WCF 数据服务的安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 1e134d877c45af00e2a2fb7e7ef0882ffd7ddc48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119114"
---
# <a name="securing-wcf-data-services"></a>WCF 数据服务的安全
本主题介绍特定于开发、 部署和运行 WCF 数据服务和应用程序支持开放数据协议 (OData) 服务的访问权限的安全注意事项。 此外应遵循有关创建安全的.NET Framework 应用程序的建议。  
  
在规划如何保护 WCF 数据服务基于 OData 服务时，必须解决身份验证过程发现和验证主体的标识和授权，确定是否已经过身份验证的主体的过程允许访问所请求的资源。 还应当考虑是否使用 SSL 来加密消息。  
  
## <a name="authenticating-client-requests"></a>对客户端请求进行身份验证  
WCF 数据服务不实现任何类型的其自己的身份验证，但是而是依赖于数据服务主机的身份验证设置。 这意味着，服务会假定它接收任何请求已经过验证由网络主机和主机已正确标识适当地通过 WCF 数据服务提供的接口的请求的原则。 多部分中详细介绍了这些身份验证选项和方法[OData 和身份验证系列](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)。  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>WCF 数据服务的身份验证选项  
 下表列出了一些可用来对发向 WCF 数据服务的请求进行身份验证的身份验证机制。  
  
|身份验证选项|描述|  
|----------------------------|-----------------|  
|匿名身份验证|启用 HTTP 匿名身份验证时，任何主体都能连接到数据服务。 匿名访问无需凭据。 仅当希望允许任何人访问数据服务时，才使用此选项。|  
|基本和摘要式身份验证|需要由用户名和密码组成的凭据以进行身份验证。 支持非 Windows 客户端的身份验证。 **安全说明：** 基本身份验证凭据（用户名和密码）以明文形式发送，会被截取。 摘要式身份验证基于所提供的凭据发送一个哈希值，因而比基本身份验证更安全。 这两者都容易受到中间人攻击。 使用这些身份验证方法时，应考虑使用安全套接字层 (SSL) 加密客户端与数据服务之间的通信。 <br /><br /> Microsoft Internet 信息服务 (IIS) 提供了这两种基本的实现，并用于 HTTP 摘要式身份验证请求中的 ASP.NET 应用程序。 该 Windows 身份验证提供程序实现允许 .NET Framework 客户端应用程序在发给数据服务的请求的 HTTP 标头中提供凭据，以无缝协商 Windows 用户的身份验证。 有关详细信息，请参阅[摘要式身份验证技术参考](https://go.microsoft.com/fwlink/?LinkId=200408)。<br /><br /> 当你想要具有你的数据服务使用基本身份验证基于某些自定义身份验证服务而不是 Windows 凭据时，则必须实现自定义 ADP.NET HTTP 模块进行身份验证。<br /><br /> 有关如何使用 WCF 数据服务使用自定义基本身份验证方案的示例，请参阅博客文章[OData 和身份验证 – 第 6 部分-自定义基本身份验证](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/)。|  
|Windows 身份验证|基于 Windows 的凭据使用 NTLM 或 Kerberos 进行交换。 该机制比基本或摘要式身份验证更安全，但它要求客户端是基于 Windows 的应用程序。 IIS 还提供对 ASP.NET 应用程序中的 HTTP 请求的 Windows 身份验证的实现。 有关详细信息，请参阅[ASP.NET 窗体身份验证概述](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100))。<br /><br /> 有关如何使用 Windows 身份验证和 WCF 数据服务的示例，请参阅博客文章[OData 和身份验证 – 第 2 部分-Windows 身份验证](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/)。|  
|ASP.NET 窗体身份验证|Forms 身份验证使你可以使用自己的代码对用户进行身份验证，然后将身份验证标记保留在 Cookie 或页的 URL 中。 您使用自己创建的登录窗体对用户的用户名和密码进行验证。 未经过身份验证的请求被重定向到登录页，用户在该页上提供凭据和提交窗体。 如果应用程序对请求进行了验证，系统会颁发一个票证，该票证包含用于重建后续请求的标识的密钥。 有关详细信息，请参阅[窗体身份验证提供程序](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100))。 **安全说明：** 默认情况下，包含窗体身份验证票证的 cookie 不安全的 ASP.NET Web 应用程序中使用窗体身份验证时。 应考虑要求使用 SSL 以保护身份验证票证和初始登录凭据。 <br /><br /> 为举例说明如何使用窗体使用 WCF 数据服务进行身份验证，请参阅博客文章[OData 和身份验证 – 一部分 7 – 窗体身份验证](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/)。|  
|基于声明的身份验证|在基于声明的身份验证，数据服务依赖于用户进行身份验证的受信任的"第三方"标识提供程序服务。 该标识提供程序对请求访问数据服务资源的用户进行肯定的身份验证并发出一个标记，授予对所请求资源的访问权限。 该标记随后提供给数据服务，后者基于与发出访问权限标记的标识服务的信任关系授予用户访问权限。<br /><br /> 使用基于声明的身份验证提供程序的优点是它们可用于跨越信任域对各种类型的客户端进行身份验证。 通过采用这样一种第三方提供程序，数据服务可以不必维护用户并对其进行身份验证，从而减轻了负担。 OAuth 2.0 是一个基于声明的身份验证协议，作为一项服务受到 Microsoft Azure AppFabric Access Control 的支持以进行联盟授权。 此协议支持基于 REST 的服务。 有关如何使用 WCF 数据服务使用 OAuth 2.0 的示例，请参阅博客文章[OData 和身份验证 – 第 8 部分-OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/)。|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>客户端库中的身份验证  
 默认情况下，WCF 数据服务客户端库不提供凭据到 OData 服务发出请求时。 如果数据服务需要登录凭据以进行用户身份验证，可以在 <xref:System.Net.NetworkCredential>（可通过 <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 属性访问）中提供凭据，如下例所示：  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 有关详细信息，请参阅[如何：数据服务请求指定客户端凭据](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)。  
  
 如果数据服务需要的登录凭据不能通过使用 <xref:System.Net.NetworkCredential> 对象（如基于声明的标记或 Cookie）指定，则必须在 HTTP 请求中手动设置标头，通常是 `Authorization` 和 `Cookie` 标头。 有关这种身份验证方案的详细信息，请参阅博客文章[OData 和身份验证 – 第 3 部分 – 客户端挂钩](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/)。 有关如何在请求消息中设置 HTTP 标头的示例，请参阅[如何：设置客户端请求中的标头](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)。  
  
## <a name="impersonation"></a>Impersonation  
 通常，数据服务使用承载数据服务的工作进程的凭据访问所需资源，如服务器上的文件或数据库。 使用模拟时，[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 应用程序可以用发出请求的用户的 Windows 标识（用户帐户）执行。 模拟通常用在依赖 IIS 进行用户身份验证的应用程序中，并使用该主体的凭据访问所需资源。 有关详细信息，请参阅[ASP.NET 模拟](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100))。  
  
## <a name="configuring-data-service-authorization"></a>配置数据服务授权  
 授权是基于之前的成功身份验证为所识别的主体或进程授予应用程序资源的访问权限。 作为一种通行做法，只应当为数据服务的用户授予刚好足够的权限以执行客户端应用程序所需的操作。  
  
### <a name="restrict-access-to-data-service-resources"></a>限制对数据服务资源的访问  
 默认情况下，WCF 数据服务，你可以授予常用读取和写入访问权限免受数据服务资源 （实体集和服务操作） 到任何用户都能够访问数据服务。 可以为数据服务公开的每个实体集分别定义用于定义读取和写入访问权限的规则。 我们建议将读取和写入访问权限仅限于客户端应用程序所需的资源。 有关详细信息，请参阅[最低资源访问要求](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)。  
  
### <a name="implement-role-based-interceptors"></a>实现基于角色的侦听器  
 侦听器可用于在数据服务对数据服务资源采取操作之前截取对它们的请求。 有关详细信息，请参阅[侦听器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。 拦截器可让您基于发出请求的已进行身份验证的用户作出授权决策。 有关如何限制对基于经过身份验证的用户标识的数据服务资源的访问的示例，请参阅[如何：截获数据服务消息](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>限制对持久数据存储区和本地资源的访问  
 用于访问持久存储区的帐户应仅授予刚好足够的数据库或文件系统权限以支持数据服务的要求。 在使用匿名身份验证时，这是用于运行宿主应用程序的帐户。 有关详细信息，请参阅[如何：开发在 IIS 上运行的 WCF 数据服务](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。 使用模拟时，必须为经过身份验证的用户授予这些资源的访问权限，通常是作为 Windows 组的一部分。  
  
## <a name="other-security-considerations"></a>其他安全注意事项  
  
### <a name="secure-the-data-in-the-payload"></a>负载中的数据安全  
OData 基于 HTTP 协议。 在 HTTP 消息中，标头可能包含重要的用户凭据，具体取决于数据服务实现的身份验证。 消息正文还可能包含必须予以保护的重要客户数据。 在这两种情况下，我们建议使用 SSL 在网络上保护此信息。  
  
### <a name="ignored-message-headers-and-cookies"></a>忽略的消息标头和 Cookie  
 除了声明内容类型和资源位置以外的 HTTP 请求标头将被忽略，数据服务永远不会设置它们。  
  
 Cookie 可作为一部分的身份验证方案，如 ASP.NET 表单身份验证。 但是，WCF DataServices 将忽略传入请求上设置的任何 HTTP cookie。 数据服务的主机可能处理该 cookie，但 WCF 数据服务运行时永远不会分析或返回 cookie。 WCF 数据服务客户端库也不会处理在响应中发送的 cookie。  
  
### <a name="custom-hosting-requirements"></a>自定义承载需求  
 默认情况下，WCF 数据服务创建为在 IIS 中托管的 ASP.NET 应用程序。 这样数据服务便可以利用该平台的安全行为。 您可以定义由自定义宿主承载的 WCF 数据服务。 有关详细信息，请参阅[承载数据服务](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)。 承载数据服务的组件和平台还必须确保以下安全行为以防范对数据服务的攻击：  
  
-   限制针对所有可能操作的数据服务请求中接受的 URI 的长度。  
  
-   限制传入和传出 HTTP 消息的大小。  
  
-   限制任何给定时间点的未完成请求的总数。  
  
-   限制 HTTP 标头及其值的大小，并提供对数据标头的 WCF 数据服务访问权限。  
  
-   检测和计数已知攻击，如 TCP SYN 和消息重播攻击。  
  
### <a name="values-are-not-further-encoded"></a>值不进一步编码  
 由 WCF 数据服务运行时发送给数据服务的属性值不进一步编码。 例如，当某个实体的字符串属性包含带格式的 HTML 内容时，数据服务不对标记进行 HTML 编码。 数据服务也不会在响应中对属性值进行进一步编码。 客户端库也不会执行任何其他编码。  
  
### <a name="considerations-for-client-applications"></a>客户端应用程序的注意事项  
 以下安全注意事项适用于使用 WCF 数据服务客户端访问 OData 服务的应用程序：  
  
-   客户端库假定用于访问数据服务的协议提供了适当安全级别。  
  
-   客户端库使用基础平台提供的传输堆栈的超时和分析选项的全部默认值。  
  
-   客户端库不从应用程序配置文件中读取任何设置。  
  
-   客户端库不实现任何跨域访问机制， 而是依赖于基础 HTTP 堆栈提供的机制。  
  
-   客户端库没有用户界面元素，并且它从不尝试显示或呈现它所接收或发送的数据。  
  
-   我们建议客户端应用程序始终对用户输入以及接受自非信任服务的数据进行验证。  
  
## <a name="see-also"></a>请参阅

- [定义 WCF 数据服务](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [WCF 数据服务客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
