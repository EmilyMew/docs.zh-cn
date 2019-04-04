---
title: 按正文路由
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: fe201161ebed66b8444c23229a6907be329d3641
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835123"
---
# <a name="route-by-body"></a>按正文路由
此示例演示如何实现一种使用任何 SOAP 操作接受消息对象的服务。 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)实现计算器服务。 该服务实现一个 `Calculate` 操作，此操作接受一个 <xref:System.ServiceModel.Channels.Message> 请求参数并返回一个 <xref:System.ServiceModel.Channels.Message> 响应。  
  
 在此示例中，客户端是一个控制台应用程序 (.exe)，并且服务承载在 IIS 中。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 此示例演示基于正文内容的消息调度。 内置的 Windows Communication Foundation (WCF) 服务模型消息调度机制基于消息的操作。 不过，有许多现有的 Web 服务使用 Action="" 来定义其所有操作。 不可能基于 WSDL 生成基于 Action 信息调度请求消息的服务。 此示例演示一个基于 WSDL 的服务协定，此 WSDL 包含在该示例包括的 Service.wsdl 中。 服务协定为计算器，与在中使用类似[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 但是，`[OperationContract]` 指定所有操作的 `Action=""`。  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 给定协定之后，服务需要自定义调度行为 `DispatchByBodyBehavior` 以便允许在操作之间调度消息。 该调度行为初始化`DispatchByBodyElementOperationSelector`具有由各自的包装器元素的 QName 进行键控的操作名称的表的自定义操作选择器。 `DispatchByBodyElementOperationSelector` 在正文第一个子级的开始标记中查找，并使用前面提到的表选择操作。  
  
 客户端使用从服务使用导出的 WSDL 自动生成的代理[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 所有操作的此 Action 均为空，这一事实对客户端节点没有影响，但自动生成的代理中的 Action 参数除外。  
  
 客户端代码执行若干计算。 运行示例时，操作请求和响应将显示在客户端控制台窗口中。 在客户端窗口中按 Enter 可以关闭客户端。  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成解决方案，请按照中的说明[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
