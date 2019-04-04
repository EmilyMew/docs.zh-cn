---
title: 元数据发布行为
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3fa806207a92e031d9015c5a8b783df4b1cc2d21
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843141"
---
# <a name="metadata-publishing-behavior"></a>元数据发布行为
“元数据发布行为”示例演示如何控制服务的元数据发布功能。 若要防止无意中泄漏可能敏感的服务元数据，Windows Communication Foundation (WCF) 服务的默认配置，请禁用元数据发布。 默认情况下此行为是安全的，但也意味着你无法使用元数据导入工具（例如 Svcutil.exe）生成调用服务所需的客户端代码，除非在配置中显式启用服务的元数据发布行为。  
  
> [!IMPORTANT]
>  为清楚起见，本示例演示如何创建不安全的元数据发布终结点。 此类终结点或许可以供未通过身份验证的匿名使用者使用，因此在部署此类终结点之前，必须谨慎以确保适合公开透露服务元数据。 请参阅[自定义安全元数据终结点](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)示例有关的示例，可以保护元数据终结点。  
  
 该示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它可以实现`ICalculator`服务协定。 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 若要使服务公开元数据，必须在服务上配置 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>。 当存在此行为时，可以通过如下方法发布元数据：配置一个终结点，将 <xref:System.ServiceModel.Description.IMetadataExchange> 协定作为 WS-MetadataExchange (MEX) 协议的实现来公开。 为方便起见，为此协定指定了缩写的配置名称“IMetadataExchange”。 此示例使用的是 `mexHttpBinding`，这是一种便于使用的标准绑定，与安全模式设置为 `wsHttpBinding` 的 `None` 等效。 使用相对地址"mex"在终结点，此操作时解决针对基本服务地址会导致终结点地址的`http://localhost/servicemodelsamples/service.svc/mex`。 下面演示了行为配置：  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 下面演示了 MEX 终结点。  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 此示例将 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 属性设置为 `true`，它还使用 HTTP GET 公开服务的元数据。 若要启用 HTTP GET 元数据终结点，服务必须具有 HTTP 基址。 在服务的基址中使用了查询字符串 `?wsdl` 以访问元数据。 例如，若要查看 Web 浏览器中服务的 WSDL 应该使用的地址`http://localhost/servicemodelsamples/service.svc?wsdl`。 或者，可以通过将 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 设置为 `true`，使用此行为通过 HTTPS 公开元数据。 这需要一个 HTTPS 基址。  
  
 若要访问服务的 MEX 终结点，请使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 这将根据服务的元数据生成一个客户端。  
  
 若要访问使用 HTTP GET 的服务的元数据，在浏览器指向`http://localhost/servicemodelsamples/service.svc?wsdl`。  
  
 如果移除此行为并尝试打开服务，将引发异常。 发生此错误是因为，如果没有该行为，使用 `IMetadataExchange` 协定配置的终结点则没有实现。  
  
 如果将 `HttpGetEnabled` 设置为 `false`，您将看到 CalculatorService 帮助页面，而不是服务的元数据。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
