---
title: IHostMemoryManager::VirtualAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5407a9d23833d73b2d6ef0038454f56f01d56867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087646"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc 方法
充当相应的 Win32 函数的逻辑包装。 Win32 实现`VirtualAlloc`保留或提交的调用进程的虚拟地址空间中的页面区域。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>参数  
 `pAddress`  
 [in]指向要分配的区域的起始地址的指针。  
  
 `dwSize`  
 [in]以字节为单位的区域的大小。  
  
 `flAllocationType`  
 [in]内存分配的类型。  
  
 `flProtect`  
 [in]区域页，并将其分配的内存保护。  
  
 `dwCriticalLevel`  
 [in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，该值指示发生分配失败的影响。  
  
 `ppMem`  
 [out]指向已分配的内存或如果无法满足请求，则为 null 的起始地址的指针。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。|  
|HOST_E_TIMEOUT|呼叫已超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|事件已取消时被阻塞的线程或纤程正在等待它。|  
|E_FAIL|发生未知的灾难性故障。 如果某方法返回 E_FAIL，CLR 不再在进程内可用。 对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|没有足够的内存已可用于完成分配请求|  
  
## <a name="remarks"></a>备注  
 在您的进程的地址空间中调用保留区域`VirtualAlloc`。 `pAddress`参数包含所需的内存块的起始地址。 此参数通常设置为 null。 操作系统将保留的可用地址范围供您的进程的记录。 一个`pAddress`的 null 值指示系统在任何它认为合适位置保留区域。 或者，您可以为内存块提供特定的起始地址。 在这两种情况下，输出参数`ppMem`作为指针返回到已分配的内存。 该函数本身返回的 HRESULT 值。  
  
 Win32`VirtualAlloc`函数没有`ppMem`参数，并改为返回指向已分配的内存的指针。 有关详细信息，请参阅 Windows 平台文档。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IHostMemoryManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
