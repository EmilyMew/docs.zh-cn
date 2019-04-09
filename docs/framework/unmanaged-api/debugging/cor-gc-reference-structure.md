---
title: COR_GC_REFERENCE 结构
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1e31e95473136bf7e7c196eacc278fa8a1caab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093652"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE 结构
包含有关要进行垃圾回收的对象的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`domain`|指向句柄或对象所属的应用程序域的指针。 其值可能为`null`。|  
|`location`|ICorDebugValue 或 ICorDebugReferenceValue 接口对应于要进行垃圾回收的对象。|  
|`type`|一个[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)枚举值，该值指示根原来所在的位置。 有关详细信息，请参阅“备注”部分。|  
|`extraData`|要进行垃圾回收的对象有关的其他数据。 此信息取决于源的对象，由`type`字段。 有关详细信息，请参阅“备注”部分。|  
  
## <a name="remarks"></a>备注  
 `type`字段是[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)枚举值，该值指示引用原来所在的位置。 特定`COR_GC_REFERENCE`值可以反映任何以下类型的托管对象：  
  
-   从所有托管堆栈的对象 (`CorGCReferenceType.CorReferenceStack`)。 这包括实时引用在托管的代码中，由公共语言运行时创建的对象。  
  
-   句柄表中的对象 (`CorGCReferenceType.CorHandle*`)。 这包括强引用 (`HNDTYPE_STRONG`和`HNDTYPE_REFCOUNT`) 和模块中的静态变量。  
  
-   终结器队列中的对象 (`CorGCReferenceType.CorReferenceFinalizer`)。 终结器队列根对象，直到运行终结器。  
  
 `extraData`字段包含额外数据，具体取决于所引用的源 （或类型）。 可能的值有：  
  
-   `DependentSource`. 如果`type`是`CorGCREferenceType.CorHandleStrongDependent`，此字段是对象保持活动状态，如果根对对象进行垃圾回收在`COR_GC_REFERENCE.Location`。  
  
-   `RefCount`. 如果`type`是`CorGCREferenceType.CorHandleStrongRefCount`，此字段是句柄的引用计数。  
  
-   `Size`. 如果`type`是`CorGCREferenceType.CorHandleStrongSizedByref`，此字段是垃圾回收器为其计算对象根的对象树的最后大小。 请注意，此计算不一定是最新。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试结构](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
