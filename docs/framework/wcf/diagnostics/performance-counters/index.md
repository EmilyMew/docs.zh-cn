---
title: WCF 性能计数器
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 31c5b386d707aa49cd36d536f1c8b419eb74a658
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087854"
---
# <a name="wcf-performance-counters"></a>WCF 性能计数器
Windows Communication Foundation (WCF) 包括大量的性能计数器，可帮助您衡量应用程序的性能。  
  
## <a name="enabling-performance-counters"></a>启用性能计数器  
 您可以启用 WCF 服务的性能计数器通过 WCF 服务的 app.config 配置文件，如下所示：  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 可以将 `performanceCounters` 属性设置为启用特定类型的性能计数器。 有效值为  
  
-   所有：启用所有类别计数器 （ServiceModelService、 ServiceModelEndpoint 和 ServiceModelOperation）。  
  
-   ServiceOnly:启用仅 ServiceModelService 类别计数器。 这是默认值。  
  
-   关闭：禁用 ServiceModel * 性能计数器。  
  
 如果你想要启用的所有 WCF 应用程序的性能计数器，您可以在 Machine.config 文件中放置配置设置。  请参阅**增加性能计数器内存大小**节在计算机上配置足够的内存性能计数器的详细信息。  
  
 如果使用 WCF 扩展点，如自定义操作调用程序，则还应发出自己的性能计数器。 这是因为如果实现了扩展点，WCF 可以不再发出的默认路径中的标准性能计数器数据。 如果未实现手动性能计数器支持，则可能看不到预期的性能计数器数据。  
  
 还可以在代码中启用性能计数器，如下所示：  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>查看性能数据  
 若要查看性能计数器捕获的数据，则可以使用 Windows 附带的性能监视器 (Perfmon.exe)。 通过转到启动该工具**启动**，然后单击**运行**并键入`perfmon.exe`在对话框中。  
  
> [!NOTE]
>  性能计数器实例可能会在终结点调度程序处理最后一条消息之前被释放。 这可能导致不能为某些消息捕获性能数据。  
  
## <a name="increasing-memory-size-for-performance-counters"></a>增加性能计数器的内存大小  
 WCF 性能计数器类别使用单独的共享的内存。  
  
 默认情况下，单独的共享内存被设置为全局性能计数器内存大小的四分之一。 默认的全局性能计数器内存大小为 524,288 字节。 因此，三种 WCF 性能计数器类别具有约 128KB 的每个默认大小。 根据计算机上的 WCF 应用程序的运行时特性，性能计数器内存可能会耗尽。 在此情况下，WCF 将错误写入到应用程序事件日志。 该错误的内容声明未加载性能计数器，并该条目包含异常"System.InvalidOperationException:自定义计数器文件视图是内存不足。" 如果在错误级别启用了跟踪，此故障也将被跟踪。 如果性能计数器内存已用尽，则继续使用已启用的性能计数器运行 WCF 应用程序可能导致性能下降。 如果您是计算机管理员，则应对计算机进行配置，以便分配足够的内存来支持随时可能存在的最大数量的性能计数器。  
  
 你可以在注册表中的 WCF 类别的性能计数器内存量。 为此，需要向以下三个位置添加名为 `FileMappingSize` 的新 DWORD 值，并将它设为所需的值（以字节为单位）。 重新启动您的计算机以使这些更改生效。  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 当释放的大量对象（例如 ServiceHost）等待进行垃圾回收时，`PrivateBytes` 性能计数器将登记一个非常大的数字。 若要解决此问题，可以添加特定于自己的应用程序的计数器，或使用 `performanceCounters` 属性仅启用服务级别计数器。  
  
## <a name="types-of-performance-counters"></a>性能计数器的类型  
 性能计数器可分为三个不同级别：服务、 终结点和操作。  
  
 可以使用 WMI 检索性能计数器实例的名称。 例如，应用于对象的  
  
-   可以通过 WMI 获得服务计数器实例名称[服务](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)实例的"CounterInstanceName"属性。  
  
-   可以通过 WMI 获取终结点计数器实例名称[终结点](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)实例的"CounterInstanceName"属性。  
  
-   可以通过 WMI 获得操作计数器实例名称[终结点](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)实例的"GetOperationCounterInstanceName"方法。  
  
 有关 WMI 的详细信息，请参阅[使用 Windows Management Instrumentation 进行诊断](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)。  
  
### <a name="service-performance-counters"></a>服务性能计数器  
 服务性能计数器将服务行为作为整体来进行衡量，可用于诊断服务整体性能。 如果使用性能监视器查看，可以在 `ServiceModelService 4.0.0.0` 性能对象下找到服务性能计数器。 使用以下模式命名计数器实例：  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 服务范围内的计数器是从终结点集合中的计数器聚合来的。  
  
 创建新的 InstanceContext 时，用于创建服务实例的性能计数器将递增。 请注意，即使在（通过现有服务）收到非激活消息时，或在从一个会话连接到实例、结束会话然后从其他会话重新进行连接时，也将创建新的 InstanceContext。  
  
### <a name="endpoint-performance-counters"></a>终结点性能计数器  
 使用终结点性能计数器可以查看反映终结点如何接受消息的数据。 使用性能监视器查看时，可在 `ServiceModelEndpoint 4.0.0.0` 性能对象下找到终结点性能计数器。 使用以下模式命名计数器实例：  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 数据与为单个操作收集的数据类似，但它只在终结点之间聚合。  
  
 终结点范围内的计数器是从操作集合中的计数器聚合来的。  
  
> [!NOTE]
>  如果两个终结点具有相同的协定名称和地址，它们将映射到同一个计数器实例中。  
  
### <a name="operation-performance-counters"></a>操作性能计数器  
 如果使用性能监视器查看，可以在 `ServiceModelOperation 4.0.0.0` 性能对象下找到操作性能计数器。 每个操作都有一个单独的实例。 也就是说，如果给定的协定具有 10 个操作，则有 10 个操作计数器实例与该协定相关联。 对象实例按下面的模式命名：  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 使用此计数器可以衡量调用的使用方式以及操作的执行情况。  
  
 当计数器在多个范围内可见时，从范围的较高一级收集到的数据会与从范围的较低一级收集到的数据相聚合。 例如，终结点处的 `Calls` 表示终结点内所有操作调用的总和；服务处的 `Calls` 表示对服务内所有终结点的所有调用的总和。  
  
> [!NOTE]
>  如果一个协定上有两个操作名称，则只能为这两个操作获取一个计数器实例。  
  
## <a name="programming-the-wcf-performance-counters"></a>对 WCF 性能计数器进行编程  
 多个文件安装在 SDK 安装文件夹，以便可以以编程方式访问 WCF 性能计数器。 下面列出了这些文件。  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 有关如何以编程方式访问计数器的详细信息，请参阅[性能计数器编程体系结构](https://go.microsoft.com/fwlink/?LinkId=95179)。  
  
## <a name="see-also"></a>请参阅

- [管理和诊断](../../../../../docs/framework/wcf/diagnostics/index.md)
