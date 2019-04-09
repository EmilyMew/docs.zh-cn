---
title: ASM_CACHE_FLAGS 枚举
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619643eb50abc75fd10d59b38767013b2617c8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077759"
---
# <a name="asmcacheflags-enumeration"></a>ASM_CACHE_FLAGS 枚举
指示由表示程序集的源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)全局程序集缓存中。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|枚举通过使用 Ngen.exe 预编译的程序集的缓存。|  
|`ASM_CACHE_GAC`|枚举在全局程序集缓存。|  
|`ASM_CACHE_DOWNLOAD`|枚举程序集已经根据需要下载或已经进行了卷影复制。|  
|`ASM_CACHE_ROOT`|指示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函数应返回路径到公共语言运行时 (CLR) 2.0 版的全局程序集缓存。 仅对的调用上下文中有意义[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。|  
|`ASM_CACHE_ROOT_EX`|指示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函数应为 CLR 版本 4 到全局程序集缓存中返回的路径。 仅对的调用上下文中有意义[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetCachePath 函数](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [IAssemblyCacheItem 接口](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [合成枚举](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
