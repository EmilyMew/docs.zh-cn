---
title: WritePropertyValue 函数 （非托管 API 参考）
description: WritePropertyValue 函数将字节写入到一个属性。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a98103367f497b18f9b8fbd61a37abf9816b8356
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107934"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 函数
将指定数量的字节写入由属性句柄标识的属性。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>语法  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>参数

`vFunc`  
[in]此参数是未使用。

`ptr`  
[in]一个指向[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)实例。

`lHandle`  
[in]一个整数，包含标识此属性的句柄。 可以通过调用来检索该句柄[GetPropertyHandle](getpropertyhandle.md)函数。   

`lNumBytes`  
[in]正在写入到的属性的字节数。 请参阅[备注](#remarks)部分，了解详细信息。

`pHandle`   
[out]指向包含数据的字节数组的指针。

## <a name="return-value"></a>返回值

此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：

|返回的常量  |“值”  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 参数不是有效的。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 出现类型不匹配。 |
|`WBEM_S_NO_ERROR` | 0 | 函数调用成功。  |
  
## <a name="remarks"></a>备注

此函数包装对的调用[IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法。

使用此函数来设置字符串和所有其他非`DWORD`或非-`QWORD`数据。

对于非字符串属性值，`lNumBytes`必须是指定的属性类型的正确的数据大小。 有关字符串属性值，`lNumBytes`必须是长度以字节为单位，指定的字符串和字符串本身必须将甚至长度以字节为单位的并且后跟一个 null 终止字符。

## <a name="requirements"></a>要求  
**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器（非托管 API 参考）](index.md)
