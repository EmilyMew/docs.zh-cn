---
title: CorTypeAttr 枚举
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e7c973ee22350f26b4f86bcc8b4c4c727291ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087282"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 枚举
包含一些值，用于指示类型元数据。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`tdVisibilityMask`|用于类型可见性信息。|  
|`tdNotPublic`|指定的类型不是在公共作用域中。|  
|`tdPublic`|指定的类型是在公共作用域中。|  
|`tdNestedPublic`|指定该类型嵌套用公共可见性。|  
|`tdNestedPrivate`|指定该类型用私有可见性嵌套。|  
|`tdNestedFamily`|指定该类型用族可见性嵌套。|  
|`tdNestedAssembly`|指定该类型嵌套可见程序集中。|  
|`tdNestedFamANDAssem`|指定该类型用族和程序集可见性嵌套。|  
|`tdNestedFamORAssem`|指定该类型用族或程序集可见性嵌套。|  
|`tdLayoutMask`|获取该类型的布局信息。|  
|`tdAutoLayout`|指定此类型的字段自动布局。|  
|`tdSequentialLayout`|指定此类型的字段顺序依次布局。|  
|`tdExplicitLayout`|指定该字段布局显式提供。|  
|`tdClassSemanticsMask`|获取有关类型的语义信息。|  
|`tdClass`|指定该类型为一个类。|  
|`tdInterface`|指定该类型为一个接口。|  
|`tdAbstract`|指定该类型为抽象类型。|  
|`tdSealed`|指定类型不能进行扩展。|  
|`tdSpecialName`|指定特殊的类名。 其名称描述如何。|  
|`tdImport`|指定导入该类型。|  
|`tdSerializable`|指定的类型是可序列化。|  
|`tdWindowsRuntime`|此类型指定为[!INCLUDE[wrt](../../../../includes/wrt-md.md)]类型。|  
|`tdStringFormatMask`|获取有关如何编码和格式字符串的信息。|  
|`tdAnsiClass`|指定此类型将解释为 ANSI LPTSTR。|  
|`tdUnicodeClass`|指定此类型将解释为 Unicode LPTSTR。|  
|`tdAutoClass`|指定此类型将 LPTSTR 自动解释。|  
|`tdCustomFormatClass`|指定该类型具有非标准编码，所指定的`CustomFormatMask`。|  
|`tdCustomFormatMask`|此掩码用于获取本机互操作的非标准编码信息。 未指定这两个位的值的含义。|  
|`tdBeforeFieldInit`|指定必须在首次尝试访问的静态字段之前初始化的类型。|  
|`tdForwarder`|指定导出的类型，和一个类型转发器。|  
|`tdReservedMask`|此标志及其以下标志由公共语言运行时内部使用。|  
|`tdRTSpecialName`|指定公共语言运行时应检查名称编码。|  
|`tdHasSecurity`|指定该类型具有与之关联的安全。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
