---
title: EApiCategories 枚举
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086450"
---
# <a name="eapicategories-enumeration"></a>EApiCategories 枚举
介绍主机可以阻止其运行部分受信任的代码中的功能的类别。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`eAll`|指定所有托管类和成员受其他`EApiCategories`字段无法在部分受信任的代码中运行。|  
|`eExternalProcessMgmt`|指定托管的类和成员允许创建、 操作和析构的外部进程的阻止在部分受信任的代码中运行。|  
|`eExternalThreading`|指定托管的类和成员允许创建、 操作和销毁外部线程的阻止在部分受信任的代码中运行。|  
|`eMayLeakOnAbort`|指定托管的类型和成员可能会泄漏内存在异常终止阻止在部分受信任的代码中运行。|  
|`eNoCategory`|指定阻止在部分受信任的代码中运行任何托管的代码类别。|  
|`eSecurityInfrastructure`|指定阻止正由部分受信任代码公共语言运行时 (CLR) 安全基础结构。|  
|`eSelfAffectingProcessMgmt`|指定托管的类和成员的功能可能会影响托管的进程阻止在部分受信任的代码中运行。|  
|`eSelfAffectingThreading`|指定托管的类和成员的功能可能会影响托管进程中的线程阻止在部分受信任的代码中运行。|  
|`eSharedState`|指定托管的类和成员公开共享的状态阻止在部分受信任的代码中运行。|  
|`eSynchronization`|指定公共语言运行时类和成员，允许用户代码持有锁阻止在部分受信任的代码中运行。|  
|`eUI`|指定托管的类和成员允许或要求人机交互禁止在部分受信任的代码中运行。|  
  
## <a name="remarks"></a>备注  
 [Iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)方法采用一个参数类型`EApiCategories`。  
  
 `EApiCategories`枚举并`SetProtectedCategories`方法并直接关系到托管<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>类。 用于托管的类<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>枚举，其值直接对应`EApiCategories`值，若要将标记公开功能与通过所述的类别相对应的托管的类型和成员`EApiCategories`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRHostProtectionManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [承载枚举](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
