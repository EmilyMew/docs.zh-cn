---
title: 默认服务行为
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 18ef0758dad9abc0c30651806957c9bb2c852abc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843053"
---
# <a name="default-service-behavior"></a>默认服务行为
此示例演示如何配置服务行为设置。 该示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它可以实现`ICalculator`服务协定。 此示例使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性来显式定义服务行为和操作行为。 你可以在配置文件中配置行为，也可以通过代码强制配置行为（如此示例所示）。  
  
 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 服务类使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 和 <xref:System.ServiceModel.OperationBehaviorAttribute> 来指定行为，如下面的代码示例所示。 指定的所有值均为默认值。  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 服务行为是使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性指定的。 下表描述了其中的一些行为。  
  
|服务行为|描述|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|在客户端的请求下自动关闭会话。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|指定每个服务实例的并发模式。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|指定实例上下文模式。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|确定是否使用所提供的同步上下文（如果已设置该上下文）。 在希望控制是否在 Windows 窗体应用程序中使用 `WindowsFormsSynchronizationContext` 时使用该上下文。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|确定是否要将常规未处理执行异常转换为 `Fault<string>` 并将其作为错误消息发送。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|指定事务的隔离级别。|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|确定意外消息头是否会导致错误。|  
  
 操作行为是使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性指定的。 下表描述了其中的一些行为。  
  
|操作行为|描述|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|确定服务操作的完成是否提交当前事务。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|确定服务操作是否在客户端流动的事务中登记。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|确定服务操作是否模拟调用方的标识。|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|确定是否在服务操作调用的开头或结尾处回收服务实例。|  
  
 运行示例时，操作请求和响应将显示在客户端控制台窗口中。 调用之间的延迟是在服务操作中对 `System.Threading.Thread.Sleep()` 进行调用的结果。 其余的行为示例更详细地说明这些行为。 在客户端窗口中按 Enter 可以关闭客户端。  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
