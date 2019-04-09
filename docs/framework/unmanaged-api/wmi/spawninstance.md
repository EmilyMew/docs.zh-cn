---
title: SpawnInstance 函数 （非托管 API 参考）
description: SpawnInstance 函数创建一个类的新实例。
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074412"
---
# <a name="spawninstance-function"></a>SpawnInstance 函数
创建类的新实例。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>参数

`vFunc`  
[in]此参数是未使用。

`ptr`  
[in]一个指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)实例。

`lFlags`  
[in] 保留。 此参数必须为 0。

`ppNewInstance`  
[out]接收到的类的新实例的指针。 如果发生错误，新对象不是返回，和`ppNewInstance`左侧不被修改。

## <a name="return-value"></a>返回值

此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：

|返回的常量  |“值”  |描述  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` 不是有效的类定义，无法生成新的实例。 不完整，或者它尚未注册到 Windows 管理通过调用[PutClassWmi](putclasswmi.md)。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 没有足够的内存是可用于完成该操作。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` 是`null`。 |
| `WBEM_S_NO_ERROR` | 0 | 函数调用成功。  |
  
## <a name="remarks"></a>备注

此函数包装对的调用[IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法。

`ptr` 必须在类定义获取从 Windows 管理。 （请注意，支持生成实例中的实例，但返回的实例为空。）然后可以使用此类定义创建新实例。 调用[PutInstanceWmi](putinstancewmi.md)函数是必需的如果你想要将实例写入 Windows 管理。

新的对象中返回`ppNewClass`自动成为当前对象的子类。 不能重写此行为。 没有其他方法可以创建子类 （的派生类）。

## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器（非托管 API 参考）](index.md)
