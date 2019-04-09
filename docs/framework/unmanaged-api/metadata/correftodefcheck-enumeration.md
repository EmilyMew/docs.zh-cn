---
title: CorRefToDefCheck 枚举
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093886"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck 枚举
指定用于控制将哪些引用项转换为相应定义以优化代码的标志。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`MDRefToDefDefault`|指定类型的引用和成员引用应转换为定义。 这是默认值 (`MDTypeRefToDef` &#124; `MDMemberRefToDef`)。|  
|`MDRefToDefAll`|指定应将所有被引用的项转换为定义。|  
|`MDRefToDefNone`|指定应将任何被引用的项转换为定义。|  
|`MDTypeRefToDef`|指定类型引用仅应将转换为类型定义。|  
|`MDMemberRefToDef`|指定成员引用仅应转换为定义。 也就是说，成员引用应转换为方法定义或字段定义。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
