---
title: ICorDebugMDA 接口
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098651"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA 接口
表示托管调试助手 (MDA) 消息。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDescription 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|获取包含此 MDA 的说明的字符串。|  
|[GetFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|获取与此 MDA 的标志。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|获取包含此 mda 名称的字符串。|  
|[GetOSThreadId 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|获取对其执行此 MDA 的操作系统线程标识符。|  
|[GetXML 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|获取与此 MDA 关联的完整 XML 流。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [使用托管调试助手诊断错误](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
