---
title: 如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: caaa89573d272c5d11d179b08c2d9e24c76d21e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140616"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点
Windows Communication Foundation (WCF) 可以创建公开支持 ASP.NET AJAX 的终结点在客户端网站上可从 JavaScript 中调用的服务。 若要创建这样的终结点，可以使用配置文件（与使用所有其他 WCF 终结点一样），或使用不要求任何配置元素的方法。 本主题演示第二种方法。  
  
 若要在不使用配置的情况下创建具有 ASP.NET AJAX 终结点的服务，则必须由 Internet 信息服务 (IIS) 来承载创建的服务。 若要激活 ASP.NET AJAX 终结点使用此方法，指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>作为 Factory 参数中[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令.svc 文件中。 此自定义工厂是一个组件，可自动将 ASP.NET AJAX 终结点配置为可以从客户端网站上的 JavaScript 中调用。  
  
 有关工作示例，请参阅[AJAX 服务而无需配置](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
 有关如何配置 ASP.NET AJAX 终结点使用配置元素的概要信息，请参阅[如何：使用配置来添加 ASP.NET AJAX 终结点](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。  
  
### <a name="to-create-a-basic-wcf-service"></a>创建基本 WCF 服务  
  
1.  使用标记的接口定义基本的 WCF 服务约定<xref:System.ServiceModel.ServiceContractAttribute>属性。 用 <xref:System.ServiceModel.OperationContractAttribute> 标记每个操作。 确保设置 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 属性。  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  使用 `ICalculator` 实现 `CalculatorService` 服务协定。  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  定义 `ICalculator` 和 `CalculatorService` 实现的命名空间，方法是将它们放置在一个命名空间块中。  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>在不使用配置的情况下在 Internet 信息服务中承载服务  
  
1.  在应用程序中创建一个名为 service 的新文件（扩展名为 .svc）。 编辑此文件添加适当的[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)服务指令信息。 指定的<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>是要在中使用[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令以自动配置 ASP.NET AJAX 终结点。  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  生成服务并从客户端调用该服务。 在调用该服务时，Internet Information Services (IIS) 会将其激活。 有关在 IIS 中承载的详细信息，请参阅[如何：承载在 IIS 中的 WCF 服务](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
### <a name="to-call-the-service"></a>调用服务  
  
1.  相对于.svc 文件的空地址处配置的终结点，因此该服务现已推出，可以在调用将请求发送到 service.svc/\<操作 >-例如，便`Add`操作。 可以通过在 ASP.NET AJAX 脚本管理器控件的“脚本”集合中输入服务 URL 来使用响应的服务。 有关示例，请参阅[AJAX 服务而无需配置](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
## <a name="example"></a>示例  
  
 在相对于基 URL 的空地址处创建自动配置的终结点。 使用此方法也可以添加和使用配置文件。 如果配置文件包含终结点定义，则这些终结点将添加到自动配置的终结点中。  
  
 例如，service.svc 使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，而服务目录包含一个 Web.config 文件，该文件在“soap”相对地址处使用 <xref:System.ServiceModel.BasicHttpBinding> 定义同一服务的终结点。 在这种情况下，服务将包括两个终结点：一个在 service.svc 处（该终结点响应 ASP.NET AJAX 请求），另一个在 service.svc/soap 处（该终结点响应 SOAP 请求）。  
  
 如果配置文件在空相对地址处定义一个终结点并且使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，则将引发异常且无法启动服务。  
  
 不能使用配置来修改自动配置终结点上的设置。 如果必须修改某些设置（如读取器配额），不得通过从 .svc 文件移除 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 并创建终结点的配置项来使用免配置方法。  
  
 如果服务要求 ASP.NET 兼容模式（例如，如果服务使用 <xref:System.Web.HttpContext> 类或 ASP.NET 授权机制），则仍需要配置文件来启用此模式。 所需的配置元素是[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)元素，它必须按如下所示添加。  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 有关详细信息，请参阅[WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)主题。  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 类是 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的派生类。 服务主机工厂机制的详细说明，请参阅[扩展托管使用 ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)主题。  
  
## <a name="see-also"></a>请参阅

- [为 ASP.NET AJAX 创建 WCF 服务](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
