---
title: 使用消息凭据的 WS 传输
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 31c1ed5d4b62c0f0b4c0c149629bb84a7dab6f01
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826205"
---
# <a name="ws-transport-with-message-credential"></a>使用消息凭据的 WS 传输
此示例演示如何将 SSL 传输安全与消息中传送的客户端凭据结合使用。 本示例使用 `wsHttpBinding` 绑定。  
  
 默认情况下，`wsHttpBinding` 绑定提供 HTTP 通信。 针对传输安全配置绑定之后，该绑定即支持 HTTPS 通信。 HTTPS 为通过网络传输的消息提供机密性和完整性保护。 但是，可用于针对服务对客户端进行身份验证的身份验证机制集仅限于 HTTPS 传输所支持的内容。 Windows Communication Foundation (WCF) 提供`TransportWithMessageCredential`旨在克服此限制的安全模式。 配置该安全模式之后，使用传输安全为传输的消息提供机密性和完整性，并执行服务身份验证。 但是，通过将客户端凭据直接置于该消息执行客户端身份验证。 这可以使用任何凭据类型，同时保持传输安全模式的性能优势的客户端身份验证的消息安全模式支持。  
  
 在此示例中，使用 `UserName` 凭据类型向服务对客户端进行身份验证。  
  
 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)实现计算器服务。 `wsHttpBinding` 绑定在客户端和服务的应用程序配置文件中指定和配置。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 此示例中的程序代码是几乎完全相同的[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)服务。 服务协定还提供了一个附加操作，即 `GetCallerIdentity`。 该操作向调用方返回调用方标识的名称。  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 必须在生成和运行示例之前使用 Web 服务器证书向导创建证书并分配此证书。 配置文件设置中的终结点定义和绑定定义可启用 `TransportWithMessageCredential` 安全模式，如下面的客户端示例配置所示。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 指定的地址使用 https:// 方案。 绑定配置将安全模式设置为 `TransportWithMessageCredential`。 必须在服务的 Web.config 文件中指定相同的安全模式。  
  
 因为此示例中使用的证书是用 Makecert.exe 创建的测试证书，安全警报出现时尝试访问 https： 地址，如`https://localhost/servicemodelsamples/service.svc`，从你的浏览器。 若要允许 WCF 客户端以使用测试证书后，某些其他代码已添加到客户端以禁用安全警报。 使用生产证书时，不需要此代码和随附的类。  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 运行示例时，操作请求和响应将显示在客户端控制台窗口中。 在客户端窗口中按 Enter 可以关闭客户端。  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  请确保您具有执行[Internet 信息服务 (IIS) 服务器证书安装说明](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
3.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
4.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
