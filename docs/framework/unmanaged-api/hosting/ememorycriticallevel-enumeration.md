---
title: EMemoryCriticalLevel 枚举
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122286"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 枚举
包含指示失败的影响，何时已请求特定的内存分配但是却无法满足的值。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`eAppDomainCritical`|指示分配已请求分配在域中执行托管的代码的关键。 如果无法分配内存，CLR 不能保证域仍可使用。 主机决定要执行不能满足分配时的操作。 它可以指示 CLR 中止`AppDomain`自动，或允许其继续运行通过调用方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。|  
|`eProcessCritical`|指示此分配是关键的过程中的托管代码执行。 使用此值是在启动期间和运行终结器时。 如果无法分配内存，CLR 不能在过程中运行。 如果分配失败时，CLR 会有效地禁用。 到 CLR 中的所有后续调用失败，并 HOST_E_CLRNOTAVAILABLE。|  
|`eTaskCritical`|指示此分配是关键到正在运行的已请求分配的任务。 如果无法分配内存，则 CLR 不能保证可以执行该任务。 出现故障时，CLR 将引发<xref:System.Threading.ThreadAbortException>物理操作系统线程上。|  
  
## <a name="remarks"></a>备注  
 在中定义的内存分配方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)并[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)接口执行此类型的参数。 根据失败的严重性，主机可以决定是否要立即失败分配请求，或等待，直到可以满足。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRMemoryNotificationCallback 接口](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [承载枚举](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
