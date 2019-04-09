---
title: QualifierSet_Next 函数 （非托管 API 参考）
description: QualifierSet_Next 函数检索枚举中的下一步限定符。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8b96957467b0acb100f7eea137b3294a60e208a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180903"
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next 函数
检索枚举中的下一个限定符，该枚举以调用 [QualifierSet_BeginEnumeration ](qualifierset-beginenumeration.md) 函数开始。   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>语法  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>参数

`vFunc`   
[in]此参数是未使用。

`ptr`   
[in]一个指向[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)实例。

`lFlags`   
[in] 保留。 此参数必须为 0。

`pstrName`   
[out]限定符的名称。 如果`null`，此参数是被忽略; 否则为`pstrName`应不指向有效`BSTR`或发生内存泄漏。 如果不为 null，该函数始终会分配一个新`BSTR`其返回`WBEM_S_NO_ERROR`。

`pVal`   
[out]成功后，限定符的值。 如果函数失败，`VARIANT`指向的`pVal`则不会修改。 如果此参数为`null`，将忽略此参数。

`plFlavor`   
[out]为接收限定符特色信息的长整型指针。 如果不想风格的信息，此参数可以是`null`。 

## <a name="return-value"></a>返回值

此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：

|返回的常量  |“值”  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 参数不是有效的。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 调用方未调用[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 没有足够的内存，可开始新的枚举。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 没有更多限定符会保留在枚举。 |
|`WBEM_S_NO_ERROR` | 0 | 函数调用成功。  |
  
## <a name="remarks"></a>备注

此函数包装对的调用[IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法。

在调用`QualifierSet_Next`函数重复合用来枚举函数返回之前所有的限定符`WBEM_S_NO_MORE_DATA`。 若要终止枚举早期，调用[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函数。

在枚举期间返回的限定符的顺序是未定义。

## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器（非托管 API 参考）](index.md)
