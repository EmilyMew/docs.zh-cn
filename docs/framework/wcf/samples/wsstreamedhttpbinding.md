---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 96dccbc971c9ef5a59557100adb6df24a745ea5d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828012"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
此示例演示如何创建一个绑定，该绑定用于在使用 HTTP 传输时支持流方案。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 下面是创建和配置新的标准绑定时涉及到的步骤。  
  
1.  创建新的标准绑定  
  
     例如，basicHttpBinding 和 netTcpBinding 的标准绑定中 Windows Communication Foundation (WCF) 配置的基础传输和通道堆栈的具体要求。 在该示例中，`WSStreamedHttpBinding` 将通道堆栈配置为支持流。 默认情况下，不将 WS-Security 和可靠消息传递添加到通道堆栈中，因为流不支持这两个功能。 新绑定是在派生自 `WSStreamedHttpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 类中实现的。 `WSStreamedHttpBinding` 包含下列绑定元素：<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 和 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。 该类提供一种 `CreateBindingElements()` 方法来配置所得到的绑定堆栈，如下面的示例代码中所示。  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  添加配置支持  
  
     为了通过配置来公开传输，此示例还实现了另外两个类：`WSStreamedHttpBindingConfigurationElement` 和 `WSStreamedHttpBindingSection`。 该类`WSStreamedHttpBindingSection`是<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>公开`WSStreamedHttpBinding`向 WCF 配置系统。 批量实现委托给从 `WSStreamedHttpBindingConfigurationElement` 派生的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。 `WSStreamedHttpBindingConfigurationElement` 类具有与 `WSStreamedHttpBinding` 的属性相对应的属性，以及用来将每个配置元素映射到绑定的函数。  
  
     可通过将以下节添加到服务的配置文件中来向配置系统注册处理程序。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     随后可以从 serviceModel 配置节中引用处理程序。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  使用以下命令安装 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  确保您已执行中列出的步骤[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  请确保您具有执行[Internet 信息服务 (IIS) 服务器证书安装说明](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
4.  若要生成解决方案，请按照中的说明[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
5.  若要跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
6.  在看到客户端窗口时，键入“Sample.txt”。 应当能够在目录中找到“Copy of Sample.txt”。  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding 示例服务  
 使用 `WSStreamedHttpBinding` 的示例服务位于服务子目录中。 所实现的 `OperationContract` 在返回 `MemoryStream` 之前，首先使用 `MemoryStream` 检索传入的流中的所有数据。 此示例服务是由 Internet 信息服务 (IIS) 承载的。  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding 示例客户端  
 在使用 `WSStreamedHttpBinding` 与服务进行交互时所用的客户端位于客户端子目录中。 因为此示例中使用的证书是用 Makecert.exe 创建的测试证书，安全警报显示当您尝试访问你的浏览器中的 HTTPS 地址，例如 https://localhost/servicemodelsamples/service.svc。 若要允许 WCF 客户端以使用测试证书后，某些其他代码已添加到客户端以禁用安全警报。 使用生产证书时，不需要此代码和随附的类。  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
