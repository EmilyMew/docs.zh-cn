---
title: CeeSectionRelocType 枚举
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119582"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 枚举
提供要影响的类型值`reloc`发出的调用中的指令[iceegen:: Addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`srRelocAbsolute`|生成仅部分相对`reloc`、 发送到.reloc 节执行任何操作。|  
|`srRelocHighLow`|生成`reloc`指针大小的位置。 这将转换为 BASED_HIGHLOW 或 BASED_DIR64 因平台而异。|  
|`srRelocHighAdj`|生成`reloc`前 32 位数字，其中后 16 位包含在.reloc 表中的下一个单词的 16 位。|  
|`srRelocMapToken`|生成令牌映射重定位，发送到.reloc 节执行任何操作。|  
|`srRelocRelative`|指示的值是相对地址链接地址信息。|  
|`srRelocFilePos`|生成仅部分相对`reloc`、 发送到.reloc 节执行任何操作。 这`reloc`是相对于部分的部分虚拟地址的文件位置。|  
|`srRelocCodeRelative`|指定代码相对地址链接地址信息。|  
|`srRelocIA64Imm64`|将生成`reloc`ia64 中的 64 位地址`movl`指令。|  
|`srRelocDir64`|生成`reloc`64 位地址。|  
|`srRelocIA64PcRel25`|生成`reloc`在 ia64 中的 25 位 PC 相对地址`br.call`指令。|  
|`srRelocIA64PcRel64`|将生成`reloc`在 ia64 中的 64 位电脑相对地址`brl.call`指令。|  
|`srRelocAbsoluteTagged`|生成 30 位部分相对`reloc`，用于标记的指针值。|  
|`srRelocSentinel`|要帮助确保任何添加到此枚举的 sentinel 值将反映到内部`reloc`名称数组。|  
|`srNoBaseReloc`|指定不发出基类`reloc`。|  
|`srRelocPtr`|一个值，该值内存预链接地址信息内容一个指针，而不是一个节偏移量。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen 接口](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
