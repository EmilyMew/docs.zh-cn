---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137210"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo 方法
提供运行时导出功能信息以帮助单步调试托管代码。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>参数  
 psz导出名  
 [输入] 如 PE 导出表中所写的运行时间导出函数名。  
  
 调用类型  
 [out]指向成员的指针[CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)描述导出的函数将如何调用托管的代码的枚举。  
  
 调用目的  
 [out]指向成员的指针[CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)描述为何导出的函数将调用托管的代码的枚举。  
  
## <a name="return-value"></a>返回值  
 该方法可以返回下表所列的值。  
  
|返回值|描述|  
|------------------|-----------------|  
|`S_OK`|方法调用成功。|  
|`E_POINTER`|`pInvokeKind` 或`pInvokePurpose`是**null**。|  
|其他失败 `HRESULT` 值。|根据需要。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此方法仅适用于 .NET Native。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>请参阅

- [“ICor调试进程6”接口](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
