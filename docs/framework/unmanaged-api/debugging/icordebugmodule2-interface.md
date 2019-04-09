---
title: ICorDebugModule2 接口
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3fb1bf3f61c78f4eb157b93363b1c06b25bee04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119894"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 接口

用作 icor 调试模块接口的逻辑扩展。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ApplyChanges 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|适用于正在运行的进程中元数据的更改和 Microsoft 中间语言 (MSIL) 代码中的更改。|  
|[GetJITCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|获取用于控制实时 (JIT) 编译的标志`ICorDebugModule2`。|  
|[ResolveAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|解析指定的元数据标记所引用的程序集。|  
|[SetJITCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|设置用于控制此 JIT 编译的标志`ICorDebugModule2`。|  
|[SetJMCStatus 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|在此设置的所有类的所有方法只是我的代码 (JMC) 状态`ICorDebugModule2`为指定的值，除中`pTokens`数组，它将设置为相反值。|  
  
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
