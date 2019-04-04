---
title: 自定义生存期
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: be6013d568e3625c5eac7e0c145db7df1c6917e3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410376"
---
# <a name="custom-lifetime"></a>自定义生存期

此示例演示如何编写一个 Windows Communication Foundation (WCF) 扩展，用于提供对共享的 WCF 服务实例的自定义生存期服务。

> [!NOTE]
> 本文的最后介绍了此示例的设置过程和生成说明。

## <a name="shared-instancing"></a>共享实例化

WCF 提供了多种实例化模式的服务实例。 本文中所述的共享实例化模式提供了一种共享多个通道之间的服务实例方法。 客户端可以联系服务中的工厂方法，并创建新的通道，以启动通信。 下面的代码段显示了客户端应用程序如何创建新的通道向现有服务实例：

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

与其他实例化模式不同，共享实例化模式拥有一种释放服务实例的独特方式。 默认情况下，当所有通道处于关闭都状态时<xref:System.ServiceModel.InstanceContext>，WCF 服务运行时检查以查看是否在服务<xref:System.ServiceModel.InstanceContextMode>配置为<xref:System.ServiceModel.InstanceContextMode.PerCall>或<xref:System.ServiceModel.InstanceContextMode.PerSession>，并且如果因此释放该实例并认领这些资源。 如果自定义<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>是正在使用，WCF 调用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>释放该实例之前的提供程序实现的方法。 如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>将返回`true`释放实例，否则<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>实现负责通知`Dispatcher`处于空闲状态通过使用回调方法。 这是通过调用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>提供程序方法。

此示例演示如何延迟释放<xref:System.ServiceModel.InstanceContext>与 20 秒的空闲超时。

## <a name="extending-the-instancecontext"></a>扩展 InstanceContext

在 WCF 中，<xref:System.ServiceModel.InstanceContext>是服务实例之间的链接和`Dispatcher`。 WCF，可通过使用其可扩展对象模式添加新状态或行为来扩展此运行时组件。 若要使用新功能扩展现有的运行时类，或者，或将新的状态功能添加到一个对象，WCF 中使用的可扩展对象模式。 可扩展对象模式中有三个接口：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。

<xref:System.ServiceModel.IExtensibleObject%601>接口由对象实现，允许使用自定义其功能的扩展。


  <xref:System.ServiceModel.IExtension%601> 接口由可作为类型为 `T` 的类扩展的对象来实现。

最后，<xref:System.ServiceModel.IExtensionCollection%601>接口是一系列<xref:System.ServiceModel.IExtension%601>实现允许检索的实现<xref:System.ServiceModel.IExtension%601>按其类型。

因此，若要将扩展<xref:System.ServiceModel.InstanceContext>，则必须实现<xref:System.ServiceModel.IExtension%601>接口。 在此示例项目中，`CustomLeaseExtension`类包含此实现。

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```


  <xref:System.ServiceModel.IExtension%601> 接口具有 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 两个方法。 顾名思义，当运行时将扩展附加到 <xref:System.ServiceModel.InstanceContext> 类的实例以及将扩展从该类的实例分离时，将会调用这两个方法。 在此示例中，`Attach` 方法用于跟踪属于当前扩展实例的 <xref:System.ServiceModel.InstanceContext> 对象。

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

此外，还必须将必要的实现添加到该扩展以提供扩展的生存期支持。 因此，`ICustomLease`接口以所需方法声明，并且在中实现`CustomLeaseExtension`类。

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

当调用 WCF<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>中的方法<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>实现中，此调用将路由到<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法的`CustomLeaseExtension`。 然后，将`CustomLeaseExtension`检查其私有状态以查看是否<xref:System.ServiceModel.InstanceContext>处于空闲状态。 如果它处于空闲状态，它将返回`true`。 否则，它将针对指定的扩展生存期启动一个计时器。

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

在该计时器的`Elapsed`事件，调度程序中的回调函数调用以启动另一个清理周期。

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

没有新消息到达实例对于转为空闲状态时续订正在运行的计时器的方法。

此示例实现 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以截获对 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的调用，并将这些调用路由到 `CustomLeaseExtension`。 
  <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 实现包含在 `CustomLifetimeLease` 类中。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF 即将发布的服务实例时调用方法。 但是，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 实现的一个实例。 这意味着无法知道如果<xref:System.ServiceModel.InstanceContext>WCF 检查当时关闭<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。 因此，此示例使用线程锁定将请求序列化到<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。

> [!IMPORTANT]
> 由于序列化可能会严重影响应用程序的性能，因此不推荐使用线程锁定方法。

中使用的私有成员字段`CustomLifetimeLease`类来跟踪处于空闲状态，并返回<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。 每次<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>调用方法时，`isIdle`返回字段并将其重置为`false`。  必须将此值设置为 `false`，以确保调度程序调用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>方法将返回`false`，调度程序通过注册一个回调函数<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>方法。 此方法将接收对所释放的 <xref:System.ServiceModel.InstanceContext> 的引用。 因此，可以查询的示例代码`ICustomLease`类型扩展，并检查`ICustomLease.IsIdle`属性扩展的状态。

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

之前`ICustomLease.IsIdle`属性为选中状态，需要设置，因为这是必需的回调属性`CustomLeaseExtension`进入空闲状态时通知调度程序。 如果 `ICustomLease.IsIdle` 返回 `true`，则 `isIdle` 私有成员仅在 `CustomLifetimeLease` 中设置为 `true`，并调用该回调方法。 由于该代码持有锁，其他线程无法更改此私有成员的值。 和下一次调度程序调用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>，它将返回`true`并让调度程序释放该实例。

由于自定义扩展的基础工作已完成，因此必须将其挂钩到服务模型。 要挂接`CustomLeaseExtension`实现<xref:System.ServiceModel.InstanceContext>，WCF 提供了<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>界面来执行的引导<xref:System.ServiceModel.InstanceContext>。 在此示例中，`CustomLeaseInitializer` 类实现此接口，并将 `CustomLeaseExtension` 的一个实例从仅方法初始化添加到 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。 此方法在初始化 <xref:System.ServiceModel.InstanceContext> 时由调度程序调用。

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 最后<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>实现挂接到服务模型使用<xref:System.ServiceModel.Description.IServiceBehavior>实现。 此实现将放置在 `CustomLeaseTimeAttribute` 类中，它还派生自 <xref:System.Attribute> 基类，以将此行为作为特性公开。

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

可使用 `CustomLeaseTime` 特性对此行为进行批注，以将其添加到示例服务类中。

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。 在每个控制台窗口中按 Enter 可以关闭服务和客户端。

### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例

1. 请确保执行了[的 Windows Communication Foundation 示例的一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。

3. 若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](running-the-samples.md)。

> [!IMPORTANT]
> 您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
