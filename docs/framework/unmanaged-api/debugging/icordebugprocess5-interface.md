---
title: ICorDebugProcess5 接口
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089225"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 接口
扩展 ICorDebugProcess 接口以支持对托管堆，以提供有关垃圾回收的托管对象信息的访问，并确定调试器是否从应用程序本地本机映像缓存加载图像。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableNGenPolicy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|设置一个值，确定如何将应用程序加载托管调试器下运行时的本机映像。|  
|[EnumerateGCReferences 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|获取要进行垃圾回收的过程中的所有对象的枚举器。|  
|[EnumerateHandles 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|获取可枚举对象句柄的进程中。|  
|[EnumerateHeap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|获取托管堆上对象的枚举器。|  
|[EnumerateHeapRegions 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|获取区域托管堆的一个枚举器。|  
|[GetArrayLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|获取内存中的布局信息的数组。|  
|[GetGCHeapInformation 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|获取一个指向[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)结构，其中包含要进行垃圾回收托管堆上对象的信息。|  
|[GetObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|获取一个指针指向一个对象托管堆上。|  
|[GetTypeFields 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|获取一个指针指向包含基于其类型标识符的类型的字段信息的数组。|  
|[GetTypeForTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|获取提供有关基于其类型标识符的对象信息的类型对象。|  
|[GetTypeID 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|获取指定地址处的对象的类型标识符。|  
|[GetTypeLayout 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|获取基于其类型标识符的内存中对象的布局信息。|  
  
## <a name="remarks"></a>备注  
 此接口进行逻辑扩展 ICorDebugProcess，ICorDebugProcess2，并[ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)接口。  
  
> [!NOTE]
>  此接口不支持从另一台计算机或另一个进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
