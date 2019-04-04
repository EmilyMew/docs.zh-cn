---
title: 预期异常
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 16b7a4029c9225984d71e5252605376d2d4b6d53
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832029"
---
# <a name="expected-exceptions"></a>预期异常
此示例演示如何在使用类型化客户端时捕获预期异常。 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)实现计算器服务。 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 此示例演示如何捕获和处理正确的程序所必须处理的两个预期异常类型：`TimeoutException` 和 `CommunicationException`。  
  
 从 Windows Communication Foundation (WCF) 客户端上的通信方法引发的异常是正常或异常。 意外异常包括灾难性故障（如 `OutOfMemoryException`）和编程错误（如 `ArgumentNullException` 或 `InvalidOperationException`）。 通常是没有有效途径来处理意外的错误，通常调用 WCF 客户端通信方法时应不捕获它们。  
  
 应从 WCF 客户端上的通信方法的例外情况包括`TimeoutException`， `CommunicationException`，和任何派生的类`CommunicationException`。 这些通信可以安全地处理通过中止 WCF 客户端并报告通信故障时表示存在问题。 因为外部因素可能导致任何应用程序中出现这些错误，所以正确的应用程序必须捕获这些异常并在发生异常时进行恢复。  
  
 客户端可以引发 `CommunicationException` 的几个派生类。 在某些情况下，应用程序也会捕获其中的某些类以执行特殊的处理，而让其他类作为 `CommunicationException` 进行处理。 这可以通过先捕获比较具体的异常类型，然后在稍后的 catch 子句中捕获 `CommunicationException` 来完成。  
  
 调用客户端通信方法的代码必须捕获 `TimeoutException` 和 `CommunicationException`。 处理此类错误的一种方法是中止客户端并报告通信故障。  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 如果发生预期异常，客户端或许可以继续使用，或许无法继续使用。 若要确定客户端是否仍然可以使用，请检查 `State` 属性是否为 `CommunicationState`.Opened。 如果此属性仍然处于打开状态，则客户端仍然可以使用。 否则，则应中止客户端并释放对其的所有引用。  
  
> [!CAUTION]
>  您可能注意到具有会话的客户端在出现异常后常常不能再使用，而没有会话的客户端在出现异常后常常可以继续使用。 但是，这些情况都是不能保证的，因此如果您希望在出现异常后继续使用客户端，您的应用程序应检查 `State` 属性以验证客户端是否仍然处于打开状态。  
  
 运行示例时，在客户端控制台窗口中显示操作响应和异常。  
  
 客户端进程运行两个方案，每个方案都尝试先调用 `Add`，再调用 `Divide`。 第一个方案通过在调用 `Divide` 之前中止客户端来模拟网络问题。 第二个方案通过将超时设置为太短的时间而使方法无法完成，从而导致超时情况的发生。 客户端进程的预期输出为：  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
