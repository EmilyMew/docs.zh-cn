---
title: CorCheckDuplicatesFor 枚举
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074867"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor 枚举
指定将检查有重复项的元数据令牌。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`MDDupAll`|检查有重复项的所有元数据标记。|  
|`MDDupENC`|未使用。|  
|`MDNoDupChecks`|不会检查有重复项的元数据标记。|  
|`MDDupTypeDef`|检查重复项的`mdTypeDef`令牌。|  
|`MDDupInterfaceImpl`|检查重复项的`mdInterfaceImpl`令牌。|  
|`MDDupMethodDef`|检查重复项的`mdMethodDef`令牌。|  
|`MDDupTypeRef`|检查重复项的`mdTypeRef`令牌。|  
|`MDDupMemberRef`|检查重复项的`mdMemberRef`令牌。|  
|`MDDupCustomAttribute`|检查重复项的`mdCustomAttribute`令牌。|  
|`MDDupParamDef`|检查重复项的`mdParamDef`令牌。|  
|`MDDupPermission`|检查重复项的`mdPermission`令牌。|  
|`MDDupProperty`|检查重复项的`mdProperty`令牌。|  
|`MDDupEvent`|检查重复项的`mdEvent`令牌。|  
|`MDDupFieldDef`|检查重复项的`mdFieldDef`令牌。|  
|`MDDupSignature`|检查重复项的`mdSignature`令牌。|  
|`MDDupModuleRef`|检查重复项的`mdModuleRef`令牌。|  
|`MDDupTypeSpec`|检查重复项的`mdTypeSpec`令牌。|  
|`MDDupImplMap`|检查重复项的`mdImplMap`令牌。|  
|`MDDupAssemblyRef`|检查重复项的`mdAssemblyRef`令牌。|  
|`MDDupFile`|检查重复项的`mdFile`令牌。|  
|`MDDupExportedType`|检查重复项的`mdExportedType`令牌。|  
|`MDDupManifestResource`|检查重复项的`mdManifestResource`令牌。|  
|`MDDupGenericParam`|检查重复项的`mdGenericParam`令牌。|  
|`MDDupMethodSpec`|检查重复项的`mdMethodSpec`令牌。|  
|`MDDupGenericParamConstraint`|检查重复项的`mdGenericParamConstraint`令牌。|  
|`MDDupAssembly`|检查重复项的`mdAssembly`令牌。|  
|`MDDupDefault`|检查重复的项`mdMemberRef`， `mdTypeRef`， `mdSignature`， `mdTypeSpec`，和`mdMethodSpec`令牌。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
