---
title: Windows 消息安全
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 49d7e74b908f0acfd13b6cd30c710034e71d667f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838581"
---
# <a name="message-security-windows"></a>Windows 消息安全
本示例演示如何将 <xref:System.ServiceModel.WSHttpBinding> 绑定配置为使用具有 Windows 身份验证的消息级安全性。 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 在此示例中，服务由 Internet 信息服务 (IIS) 承载，客户端是一个控制台应用程序 (.exe)。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 默认安全设置[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)是使用 Windows 身份验证的消息安全。 此示例中的配置文件显式设置`mode`的属性[\<安全 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)到`Message`并`clientCredentialType`属性为`Windows`。 这些值是此绑定的默认值，但为了演示其用法，已对这些值进行了显式配置，如下面的示例配置所示。  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 客户端终结点配置由服务终结点的绝对地址、绑定和协定组成。 该客户端绑定是使用相应的 `securityMode` 和 `authenticationMode` 配置的。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 为了演示如何使用 <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> 来访问调用方的标识，服务源代码已进行了修改。  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 运行示例时，操作请求和响应将显示在客户端控制台窗口中。 调用的第一个方法 `GetCallerIdentity` 将调用方标识的名称返回给客户端。 在控制台窗口中按 Enter 可以关闭客户端。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
