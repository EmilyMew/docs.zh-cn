---
title: ICorDebugObjectValue::GetFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107908"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue 方法
获取此对象值的指定类的指定字段的值。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>参数  
 `pClass`  
 [in]指向"ICorDebugClass"对象，表示要为其获取字段值的类的指针。  
  
 `fieldDef`  
 [in]`mdFieldDef`引用描述字段的元数据的令牌。  
  
 `ppValue`  
 [out]指向一个"ICorDebugValue"对象，表示指定字段的值的指针。  
  
## <a name="remarks"></a>备注  
 中指定类`pClass`参数，必须是对象值的类的层次结构中，此字段必须是该类的字段。  
  
 `GetFieldValue`方法仍将成功为泛型对象和泛型类。 例如，如果 MyDictionary\<V > 继承自字典\<字符串，V >，且对象值的类型 MyDictionary\<int32 >，并传递`ICorDebugClass`字典对象\<K，V > 将已成功获取字典中的字段\<string，int32 >。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅
