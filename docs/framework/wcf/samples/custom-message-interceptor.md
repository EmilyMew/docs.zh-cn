---
title: 自定义消息拦截器
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 789b3a2003ab96a9658eab7c092067e6110a46cd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824775"
---
# <a name="custom-message-interceptor"></a>自定义消息拦截器
此示例演示通道扩展模型的使用。 特别是，演示如何实现可创建通道工厂和通道侦听器的自定义绑定元素，以便在运行时堆栈的特定点截获所有传入和传出消息。 此示例还包括一个客户端和一个服务器，用于演示这些自定义工厂的使用。  
  
 在此示例中，客户端和服务都是控制台程序 (.exe)。 客户端和服务都使用一个通用库 (.dll)，其中包含自定义绑定元素及其关联的运行库对象。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 此示例介绍了使用通道框架并遵循 WCF 最佳做法在 Windows Communication Foundation (WCF) 创建自定义分层的通道的推荐的过程。 创建自定义分层通道的步骤如下所示：  
  
1.  确定您的通道工厂和通道侦听器将要支持哪些通道形状。  
  
2.  创建支持您的通道形状的通道工厂和通道侦听器。  
  
3.  添加一个绑定元素，用于将自定义分层通道添加到通道堆栈中。  
  
4.  添加一个绑定元素扩展部分，以便将新的绑定元素公开到配置系统。  
  
## <a name="channel-shapes"></a>通道形状  
 编写自定义分层通道的第一步是确定该通道需要哪些形状。 对于我们的消息拦截器，支持我们下面的层所支持的任何形状（例如，如果我们下面的层可以生成 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>，则我们也公开 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>）。  
  
## <a name="channel-factory-and-listener-factory"></a>通道工厂和侦听器工厂  
 编写自定义分层通道的下一步是为客户端通道创建 <xref:System.ServiceModel.Channels.IChannelFactory> 的实现，并为服务通道创建 <xref:System.ServiceModel.Channels.IChannelListener> 的实现。  
  
 这些类采用内部工厂和侦听器，并将除 `OnCreateChannel` 和 `OnAcceptChannel` 之外的所有调用委托给内部工厂和侦听器。  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>添加绑定元素  
 此示例定义了一个自定义绑定元素：`InterceptingBindingElement`。 `InterceptingBindingElement` 采用`ChannelMessageInterceptor`作为输入，并使用此`ChannelMessageInterceptor`来处理通过它传递的消息。 这是唯一必须公开的类。 工厂、侦听器和通道都可以是公共运行库接口的内部实现。  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>添加配置支持  
 为了与绑定配置集成，库定义了一个配置节处理程序作为绑定元素扩展部分。 客户端和服务器配置文件必须向配置系统注册该绑定元素扩展。 希望将其绑定元素公开给配置系统的实现程序可以从此类派生。  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>添加策略  
 为了与我们的策略系统集成，`InterceptingBindingElement` 实现了 IPolicyExportExtension，以表明我们应参与生成策略。 若要支持在生成的客户端导入策略，用户可以注册 `InterceptingBindingElementImporter` 的派生类并重写 `CreateMessageInterceptor`()，以生成启用策略的 `ChannelMessageInterceptor` 类。  
  
## <a name="example-droppable-message-inspector"></a>示例:消息拦截器  
 此示例中包括了丢弃消息的 `ChannelMessageInspector` 的示例实现。  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 您可以按如下方式从配置中访问该示例：  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"   
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 客户端和服务器都使用这个新创建的配置部分，将自定义工厂插入其运行库通道堆栈的最低层（在传输层之上）。  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 客户端使用 `MessageInterceptor` 库在编号为偶数的消息中添加一个自定义头。 另一方面，服务则使用 `MessageInterceptor` 库丢弃所有没有这个特殊头的消息。  
  
 运行服务后再运行客户端，您应该可以看到以下客户端输出。  
  
```  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 客户端向服务报告了 10 个不同的风速，但只用这个特殊的头标记了其中 5 个。  
  
 在服务上，您应看到以下输出：  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  使用以下命令安装 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  若要生成解决方案，请按照中的说明[生成 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
5.  先运行 Service.exe，然后运行 Client.exe 并观察两个控制台窗口的输出。  
  
