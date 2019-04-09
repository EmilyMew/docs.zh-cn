---
title: CorAssemblyFlags 枚举
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072709"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags 枚举
包含一些值，用于描述应用于程序集编译的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`afPublicKey`|指示程序集引用包含完整的、 未经哈希的公钥。|  
|`afPA_None`|指示未指定的处理器体系结构。|  
|`afPA_MSIL`|指示处理器体系结构为非特定 (PE32)。|  
|`afPA_x86`|指示处理器体系结构 x86 (PE32)。|  
|`afPA_IA64`|指示处理器体系结构为 Itanium （PE32 +）。|  
|`afPA_AMD64`|指示处理器体系结构是 AMD X64 （PE32 +）。|  
|`afPA_ARM`|指示处理器体系结构是 ARM (PE32)。|  
|`afPA_NoPlatform`|指示程序集是引用程序集;也就是说，它适用于任何体系结构，但无法在任何体系结构上运行。 因此，该标志是与相同`afPA_Mask`。|  
|`afPA_Specified`|指示处理器体系结构标志应将传播给`AssemblyRef`记录。|  
|`afPA_Mask`|一个掩码，用于描述处理器体系结构。|  
|`afPA_FullMask`|指定包含处理器体系结构说明。|  
|`afPA_Shift`|指示处理器体系结构标志到和从索引中的 shift 计数。|  
|`afEnableJITcompileTracking`|指示相应的值从<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afDisableJITcompileOptimizer`|指示相应的值从<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。|  
|`afRetargetable`|指示程序集可以对程序集从不同的发布服务器在运行时重定向。|  
|`afContentType_Mask`|一个屏蔽，它描述的内容类型。|  
|`afContentType_Default`|指示默认内容类型。|  
|`afContentType_WindowsRuntime`|指示[!INCLUDE[wrt](../../../../includes/wrt-md.md)]内容类型。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
