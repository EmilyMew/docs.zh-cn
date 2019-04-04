---
title: 实例化初始化
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ec44276d56b0a914c742a5a709f2207f8111e57b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827908"
---
# <a name="instancing-initialization"></a>实例化初始化
此示例扩展[池](../../../../docs/framework/wcf/samples/pooling.md)示例通过定义一个接口， `IObjectControl`，这通过激活和停用它来自定义对象的初始化。 客户端调用向池中返回对象以及不向池中返回对象的方法。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
## <a name="extensibility-points"></a>扩展点  
 创建 Windows Communication Foundation (WCF) 扩展的第一步是决定要使用的可扩展性点。 在 WCF 中，术语*EndpointDispatcher*指的运行时组件负责将传入消息转换成用户服务上的方法调用，并将该方法的返回值转换成传出消息. WCF 服务创建一个 EndpointDispatcher 每个终结点。  
  
 EndpointDispatcher 使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 类提供终结点范围（适用于服务收到或发送的所有消息）的扩展。 通过此类可以自定义控制 EndpointDispatcher 行为的各种属性。 本示例重点介绍 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 属性，该属性指向提供服务类实例的对象。  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 在 WCF 中，EndpointDispatcher 通过来创建服务类的实例的实例提供程序实现<xref:System.ServiceModel.Dispatcher.IInstanceProvider>接口。 此接口只有两个方法：  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>：当消息到达时，调度程序调用<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>方法来创建服务类来处理该消息的实例。 调用此方法的频率由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性决定。 例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性设置为 <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>，则创建服务类的一个新实例来处理到达的每个消息，因此每当有消息到达时，都会调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>。  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>：当服务实例处理完该消息时，EndpointDispatcher 将调用<xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>方法。 与 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法中一样，调用此方法的频率由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性决定。  
  
## <a name="the-object-pool"></a>对象池  
 `ObjectPoolInstanceProvider` 类包含对象池的实现。 此类实现 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 接口，以便与服务模型层进行交互。 当 EndpointDispatcher 调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法时，自定义实现将在内存中的池内寻找现有对象，而不是创建新的实例。 如果找到一个对象，则返回该对象。 否则，`ObjectPoolInstanceProvider` 则检查 `ActiveObjectsCount` 属性（从池中返回的对象数）是否已达到最大池大小。 如果没有达到最大池大小，则创建一个新实例并将其返回调用方，而 `ActiveObjectsCount` 则相应地增加。 否则，对象创建请求将排队，等待配置的时间段。 下面的示例代码演示了 `GetObjectFromThePool` 的实现。  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 自定义 `ReleaseInstance` 实现将已释放的实例重新添加回池中并减少 `ActiveObjectsCount` 值。 EndpointDispatcher 可以从不同的线程调用这些方法，因此需要同步访问 `ObjectPoolInstanceProvider` 类中的类级别成员。  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 `ReleaseInstance`方法提供*清除初始化*功能。 通常，该池为其生存期保持最少数量的对象。 但是，可能有过度使用的时期，此时需要在池中创建更多对象以达到配置中指定的最大限制。 最终，当池变得不是很活跃时，那些多余的对象可能会变成额外的开销。 因此，当 `activeObjectsCount` 达到 0 时，会启动一个空闲计时器，该计时器将触发并执行清除循环。  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 使用以下行为对 ServiceModel 层扩展进行挂钩：  
  
-   服务行为：这些行为允许自定义整个服务运行时。  
  
-   终结点行为：这些行为允许自定义特定服务终结点，包括 EndpointDispatcher。  
  
-   协定行为：这些行为允许自定义<xref:System.ServiceModel.Dispatcher.ClientRuntime>或<xref:System.ServiceModel.Dispatcher.DispatchRuntime>分别是在客户端或服务类。  
  
-   操作行为：这些行为允许自定义<xref:System.ServiceModel.Dispatcher.ClientOperation>或<xref:System.ServiceModel.Dispatcher.DispatchOperation>分别是在客户端或服务类。  
  
 为了实现对象池扩展，可以创建终结点行为或服务行为。 在此示例中，我们使用了服务行为，它使服务的每个终结点都具有对象池能力。 服务行为是通过实现 <xref:System.ServiceModel.Description.IServiceBehavior> 接口创建的。 可以通过多种方式让 ServiceModel 注意到自定义行为：  
  
-   使用自定义属性。  
  
-   强制将它添加到服务说明的行为集合中。  
  
-   扩展配置文件。  
  
 本示例使用自定义属性。 构造 <xref:System.ServiceModel.ServiceHost> 后，它检查服务类型定义中使用的属性并将可用行为添加到服务说明的行为集合中。  
  
 <xref:System.ServiceModel.Description.IServiceBehavior>接口有三个方法： <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,`和<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>。 由 WCF 调用这些方法时<xref:System.ServiceModel.ServiceHost>正在初始化。 首先调用 <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>；它允许检查服务的一致性。 然后调用 <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>；只有非常高级的方案才需要此方法。 最后调用 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>，它负责配置运行时。 下面的参数传递给 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>：  
  
-   `Description`：此参数提供整个服务的服务说明。 它可用于检查有关服务的终结点、协定、绑定和其他关联数据的说明数据。  
  
-   `ServiceHostBase`：此参数提供<xref:System.ServiceModel.ServiceHostBase>，当前正在初始化。  
  
 在自定义 <xref:System.ServiceModel.Description.IServiceBehavior> 实现中，会实例化 `ObjectPoolInstanceProvider` 的一个新实例，并将其分配给附加到 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 的每个 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 的 <xref:System.ServiceModel.ServiceHostBase> 属性。  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 除了 <xref:System.ServiceModel.Description.IServiceBehavior> 实现外，`ObjectPoolingAttribute` 类有多个可以使用属性自变量自定义对象池的成员。 这些成员包括 `MaxSize`、`MinSize`、`Enabled` 和 `CreationTimeout`，用于匹配 .NET 企业服务提供的对象池功能集。  
  
 对象池行为现在的 WCF 服务通过对使用新创建的自定义的服务实现进行批注添加`ObjectPooling`属性。  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>挂钩激活和停用  
 对象池的主要目的是通过代价相对较高的创建和初始化来优化生存期较短的对象。 因此，如果使用得当，它可以显著提高应用程序的性能。 因为对象是从池中返回的，所以只调用构造函数一次。 但是，有些应用程序需要某种级别的控制，以便初始化和清除单一上下文中使用的资源。 例如，用于一组计算的某个对象可以在处理下一个计算之前重置其私有字段。 企业服务通过允许对象开发人员重写 `Activate` 基类中的 `Deactivate` 和 <xref:System.EnterpriseServices.ServicedComponent> 方法，实现了这种上下文特定的初始化。  
  
 对象池就在从池中返回对象之前调用 `Activate` 方法。 当对象重新返回到池中后，将调用 `Deactivate`。 <xref:System.EnterpriseServices.ServicedComponent> 基类还有一个称为 `boolean` 的 `CanBePooled` 属性，它可用于通知池是否可以对对象进一步进行池处理。  
  
 为了模拟此功能，此示例声明了一个具有上述成员的公共接口 (`IObjectControl`)。 此接口然后由用来提供上下文特定初始化的服务类来实现。 必须修改 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 实现才能满足这些要求。 现在，每次调用可获取对象`GetInstance`方法，必须检查该对象是否实现`IObjectControl.`如果是这样，您必须调用`Activate`方法正确。  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 将对象返回池中时，需要在将对象添加回池之前检查 `CanBePooled` 属性。  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 因为服务开发人员可以决定对象是否可以进行池处理，所以池中的对象计数在给定时间可以低于最小大小。 因此，您必须检查对象计数是否低于最小水平，并在清除过程中执行必要的初始化。  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 运行示例时，操作请求和响应将显示在服务和客户端控制台窗口中。 在每个控制台窗口中按 Enter 可以关闭服务和客户端。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
