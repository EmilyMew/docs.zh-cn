---
title: QualifierSet_BeginEnumeration 函数 （非托管 API 参考）
description: QualifierSet_BeginEnumeration 函数重置对象的限定符的枚举的器。
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375410"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration 函数

将对象限定符的枚举器重置到枚举的起始处。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>语法

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>参数

`vFunc`\
[in]此参数是未使用。

`ptr`\
[in]一个指向[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)实例。

`lFlags`\
[in]值中所述的标志的按位组合[备注](#remarks)节指定要包括在枚举中的限定符。

## <a name="return-value"></a>返回值

此函数返回以下值中定义*WbemCli.h*标头文件，也可以在定义它们为常量在代码中：

|返回的常量  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` 参数无效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次调用`QualifierSet_BeginEnumeration`而无需对的干预调用进行[ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 没有足够的内存，可开始新的枚举。 |
|`WBEM_S_NO_ERROR` | 0 | 函数调用成功。  |

## <a name="remarks"></a>备注

此函数包装对的调用[IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)方法。

若要枚举所有对象上的限定符，调用此方法必须在首次调用前[QualifierSet_Next](qualifierset-next.md)。 保证在其中枚举了限定符的顺序是固定的给定的枚举。

可以作为传递的标志`lEnumFlags`中定义参数*WbemCli.h*标头文件，也可以在定义它们为常量在代码中。

|返回的常量  |值  |描述  |
|---------|---------|---------|
|  | 0 | 返回所有限定符的名称。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 返回限定符的名称特定于当前的属性或对象。 <br/> 属性：返回仅特定于 （包括重写） 的属性限定符，而不从类定义传播这些限定符。 <br/> 实例：返回的是仅特定于实例的限定符名称。 <br/> 类：要派生的类的特定返回仅限定符。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 返回名称的列是限定符传播从另一个对象。 <br/> 属性：返回时仅限定符传播给此属性从类定义中，而不从该属性本身。 <br/> 实例：仅这些限定符传播从返回的类定义。 <br/> 类：返回从父类继承仅这些限定符名称。 |

## <a name="requirements"></a>要求

**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。

**标头：** WMINet_Utils.idl

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>请参阅

- [WMI 和性能计数器 （非托管 API 参考）](index.md)