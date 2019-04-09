---
title: IDENTITY_ATTRIBUTE 结构
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107336"
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE 结构
包含有关属性的元数据信息[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)实例。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`pszNamespace`|指向以 null 结尾的字符字符串，包含命名空间的该属性为中。|  
|`pszName`|指向包含的属性的名称的以 null 结尾的字符字符串的指针。|  
|`pszValue`|指向包含该属性的值的以 null 结尾的字符字符串的指针。|  
  
## <a name="remarks"></a>备注  
 `IDENTITY_ATTRIBUTE`结构包含三个指向以 null 结尾的字符串。 这三个字符串描述一个属性。  
  
 实例`IDENTITY_ATTRIBUTE`结构是与实例相关联[IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)结构。 `IDENTITY_ATTRIBUTE`结构包含实际的字符串，并相应`IDENTITY_ATTRIBUTE_BLOB`结构列出了为中列出的三个字符串的偏移量`IDENTITY_ATTRIBUTE`结构。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Isolation.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IDefinitionIdentity 接口](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB 结构](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [合成结构](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
