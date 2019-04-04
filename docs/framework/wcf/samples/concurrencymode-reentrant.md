---
title: 可重入的 ConcurrencyMode
ms.date: 03/30/2017
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
ms.openlocfilehash: 2daa802d72a08d31a52a09952d31b718e8a51a90
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816625"
---
# <a name="concurrencymode-reentrant"></a>可重入的 ConcurrencyMode
本示例演示对服务实现使用 ConcurrencyMode.Reentrant 的必要性和含义。 ConcurrencyMode.Reentrant 暗示服务（或回调）只在给定时间处理一个消息（类似于 `ConcurencyMode.Single`）。 若要确保线程安全，Windows Communication Foundation (WCF) 锁定`InstanceContext`处理一条消息，以便可以处理任何其他消息。 在处于可重入模式的情况下，`InstanceContext` 将仅在服务进行传出调用之前解除锁定，从而允许后续调用（可按示例中的演示重入），并在下次进入服务时被锁定。 为了演示此行为，示例演示了客户端和服务如何使用双工协定相互发送消息。  
  
 定义的协定是双工协定，其 `Ping` 方法由服务实现，其回调方法 `Pong` 由客户端实现。 客户端用滴答计数调用服务的 `Ping` 方法，从而启动调用。 服务检查滴答计数是否等于 0，然后调用回调 `Pong` 方法，同时递减滴答计数。 以上过程通过示例中的以下代码完成。  
  
```csharp
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
```  
  
 回调的 `Pong` 实现与 `Ping` 实现具有相同的逻辑。 也就是说，该实现检查滴答计数是否不为零，然后对回调通道（在本例中为用于发送原始 `Ping` 消息的通道）调用 `Ping` 方法，并使滴答计数减 1。 当滴答计数达到 0 时，该方法返回，从而将所有回复解包回启动该调用的客户端进行的第一个调用。 回调实现中显示了此过程。  
  
```csharp
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
```  
  
 `Ping` 和 `Pong` 方法都是请求/答复，这意味着对 `Ping` 的调用返回前，对 `CallbackChannel<T>.Pong()` 的第一个调用不会返回。 在客户端上，在由 `Pong` 方法进行的下一个 `Ping` 调用返回前，该方法不会返回。 由于回调和服务在答复挂起请求之前，必须进行传出请求/答复调用，因此这两个实现必须使用 ConcurrencyMode.Reentrant 行为进行标记。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="demonstrates"></a>演示  
 若要运行示例，请生成客户端和服务器项目。 然后打开两个命令窗口，并将目录更改为\<示例 > \CS\Service\bin\debug 和\<示例 > \CS\Client\bin\debug 目录。 然后启动该服务通过键入`service.exe`和调用的计时周期数作为输入参数传递的初始值 Client.exe。 显示了 10 次滴答的示例输出。  
  
```console  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
```  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
