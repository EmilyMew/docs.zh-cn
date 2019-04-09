---
title: CLR_DEBUGGING_VERSION 结构
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87f938a7119abe4a88da65bd779a5f4a02499516
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117113"
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION 结构
出于调试目的，定义公共语言运行时 (CLR) 的产品版本。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`wStructVersion`|结构版本数|  
|`wMajor`|主版本号。|  
|`wMinor`|次版本号。|  
|`wBuild`|内部版本号。|  
|`wRevision`|修订号。|  
  
## <a name="remarks"></a>备注  
 `CLR_DEBUGGING_VERSION`结构但是是 COR_VERSION 结构相同，则`CLR_DEBUGGING_VERSION`结构提供了其他结构版本字段 (`wStructVersion`)。 目前，此字段必须设置为零。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试结构](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
