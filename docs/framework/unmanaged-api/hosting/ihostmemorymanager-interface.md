---
title: IHostMemoryManager 接口
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137346"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager 接口
而不是使用标准 Win32 虚拟内存函数提供允许公共语言运行时 (CLR)，以便通过主机的虚拟内存请求的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|通知宿主公共语言运行时 (CLR) 已获得从操作系统指定的内存。|  
|[CreateMAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|获取到的接口指针[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用于从堆创建主机的请求的内存分配的实例。|  
|[GetMemoryLoad 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|由主机的报告获取当前正在使用的物理内存量。|  
|[NeedsVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|通知宿主，CLR 会尝试使用指定的内存。|  
|[RegisterMemoryNotificationCallback 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|注册到通知的计算机上的当前内存负载的 CLR 宿主通过调用的回调函数的指针。|  
|[ReleasedVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|通知宿主 CLR 已完成使用指定的内存。|  
|[VirtualAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|充当相应的 Win32 函数，将保留或提交的调用进程的虚拟地址空间中的页面区域的逻辑包装器。|  
|[VirtualFree 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|充当相应的 Win32 函数，从而释放，解除，或释放并解除调用进程虚拟地址空间中的页面区域的逻辑包装器。|  
|[VirtualProtect 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|充当相应的 Win32 函数，这会更改调用进程的虚拟地址空间中的提交页面的保护区域上的逻辑包装器。|  
|[VirtualQuery 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|充当相应的 Win32 函数检索有关调用进程的虚拟地址空间中的页范围的信息的逻辑包装器。|  
  
## <a name="remarks"></a>备注  
 `IHostMemoryManager` 此外提供了方法，以便 CLR 获取要在堆上发出内存请求和获取在过程中，内存压力的级别中的指针，如报告的主机。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IHostMalloc 接口](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
