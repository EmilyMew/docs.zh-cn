---
title: 使用复杂类型的 AJAX 服务示例
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 54d8c90f8317b69195401eda64e8a482aaf8460a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128500"
---
# <a name="ajax-service-using-complex-types-sample"></a>使用复杂类型的 AJAX 服务示例
此示例演示如何使用 Windows Communication Foundation (WCF) 来创建用于创建复杂类型的实例，并将其发送服务和客户端作为 JavaScript 对象表示法 (JSON) 之间的 ASP.NET 异步 JavaScript 和 XML (AJAX) 服务。 可以从 Web 浏览器客户端使用 JavaScript 代码来访问 AJAX 服务。 此示例是基于[基本 AJAX 服务](../../../../docs/framework/wcf/samples/basic-ajax-service.md)示例。  
  
 WCF 中的 AJAX 支持适用于与通过 ASP.NET AJAX 一起使用<xref:System.Web.UI.ScriptManager>控件。 使用 ASP.NET AJAX 使用 WCF 的示例，请参阅[AJAX 示例](ajax.md)。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 下面的示例中的服务是无代码的特定于 AJAX 的 WCF 服务。 由于未应用 <xref:System.ServiceModel.Web.WebGetAttribute> 属性，因此将使用默认的 HTTP 谓词（“POST”）。 该服务有一个操作 `DoMath`，该操作返回一个名为 `MathResult` 的复杂类型。 该复杂类型是标准的数据协定类型，也不包含特定于 AJAX 的代码。  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 通过使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 在服务上创建 AJAX 终结点，就像在基本 AJAX 服务示例中一样。  
  
 客户端网页 ComplexTypeClientPage.aspx 包含 ASP.NET 和 JavaScript 代码来调用服务，当用户单击**执行计算**页上的按钮。 用于调用服务的代码构造 JSON 正文并发送它使用 HTTP POST，类似于[使用 HTTP POST 的 AJAX 服务](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)示例。  
  
 在服务调用成功之后，您可以在所得到的 JavaScript 对象上访问各个数据成员（`sum`、`difference`、`product` 和 `quotient`）。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如中所述生成解决方案 ComplexTypeAjaxService.sln[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  导航到`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`（不要打开 ComplexTypeClientPage.aspx 在浏览器中从项目目录中）。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>请参阅

- [基本 AJAX 服务](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
