---
title: 会话
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 32a81ba462eccfc6f4ba2a694793895810074b7e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817027"
---
# <a name="session"></a>会话
“会话”示例演示如何实现需要会话的协定。 会话提供用来执行多个操作的上下文。 这允许服务将某个状态与给定的会话相关联，从而使后续操作可以使用上一个操作的状态。 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它可实现计算器服务。 `ICalculator` 协定已进行修改，允许在保持运行结果的同时执行一组算术运算。 此功能由 `ICalculatorSession` 协定定义。 服务在调用多个服务操作以执行一个计算时维护客户端的状态。 客户端可以通过调用 `Result()` 来检索当前结果，通过调用 `Clear()` 将结果清零。  
  
 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 将协定的 <xref:System.ServiceModel.SessionMode> 设置为 `Required` 可以确保在通过特定的绑定公开该协定时，该绑定支持会话。 如果绑定不支持会话，则会引发异常。 定义 `ICalculatorSession` 接口使得可以调用一个或多个修改运行结果的操作，如下面的示例代码所示。  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 服务使用 <xref:System.ServiceModel.InstanceContextMode> 的 <xref:System.ServiceModel.InstanceContextMode.PerSession> 将给定的服务实例上下文绑定到每个传入会话。 这使服务可以在本地成员变量中维护每个会话的运行结果。  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 运行示例时，客户端会向服务器发出几个请求并请求结果，结果然后显示在客户端控制台窗口中。 在客户端窗口中按 Enter 可以关闭客户端。  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
