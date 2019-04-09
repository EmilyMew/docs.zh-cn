---
title: COR_TYPEID 结构
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109858"
---
# <a name="cortypeid-structure"></a>COR_TYPEID 结构
包含类型标识符。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`token1`|第一个标记。|  
|`token2`|第二个标记。|  
  
## <a name="remarks"></a>备注  
 `COR_TYPEID`结构返回的大量调试方法，提供要进行垃圾回收的对象有关的信息。 它可以然后作为参数传递到其他调试方法，提供与项相关的其他信息。 例如，通过枚举[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)对象，您可以检索各个[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)表示托管堆上的单个对象的对象。 然后，可以传递`COR_TYPEID`值从`COR_HEAPOBJECT.type`字段[ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法来检索一个 ICorDebugType 对象，提供有关对象的类型信息。  
  
 一个`COR_TYPEID`旨在不透明对象。 其各个字段不应访问或操作。 其唯一用途是作为提供的标识符作为`out`中参数的方法调用和可，反过来，传递给其他方法，以提供其他信息。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试结构](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
