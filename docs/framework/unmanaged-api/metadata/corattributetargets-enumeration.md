---
title: CorAttributeTargets 枚举
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49784a0eba0458a7b9ddbcd58cbe1a187c3c779a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101182"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets 枚举
指定可应用属性的应用程序元素。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`catAssembly`|特性可以应用于程序集。|  
|`catModule`|特性可以应用于可移植可执行文件 （.dll 或.exe） 模块。|  
|`catClass`|特性可以应用于类。|  
|`catStruct`|特性可以应用于结构;也就是说，类型的值。|  
|`catEnum`|特性可以应用于枚举。|  
|`catConstructor`|特性可以应用于构造函数。|  
|`catMethod`|特性可以应用于方法。|  
|`catProperty`|特性可以应用于属性。|  
|`catField`|特性可以应用于字段。|  
|`catEvent`|特性可以应用于事件。|  
|`catInterface`|特性可以应用于接口。|  
|`catParameter`|属性可以应用于参数。|  
|`catDelegate`|可以对委托应用属性。|  
|`catGenericParameter`|特性可以应用于泛型参数。|  
|`catAll`|特性可以应用于任何应用程序元素。|  
|`catClassMembers`|特性可以应用于类的成员。|  
  
## <a name="remarks"></a>备注  
 `CorAttributeTargets`枚举值可以组合使用位或运算来获得首选的组合。  
  
 `CorAttributeTargets`与托管<xref:System.AttributeTargets?displayProperty=nameWithType>枚举。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
