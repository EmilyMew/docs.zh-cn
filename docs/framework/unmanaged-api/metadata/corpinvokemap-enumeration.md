---
title: CorPinvokeMap 枚举
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079625"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 枚举
指定选项的 PInvoke 调用。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`pmNoMangle`|使用指定的每个成员名称。|  
|`pmCharSetMask`|保留。|  
|`pmCharSetNotSpec`|保留。|  
|`pmCharSetAnsi`|以多字节字符串的形式封送字符串。|  
|`pmCharSetUnicode`|以 Unicode 2 字节字符的形式封送字符串。|  
|`pmCharSetAuto`|针对目标操作系统适当地自动封送字符串。 默认值是 Windows NT、 Windows 2000、 Windows XP 和 Windows Server 2003 系列中; 上的为 Unicode默认值为 ANSI，在 Windows 98 和 Windows me 一起提供。|  
|`pmBestFitUseAssem`|保留。|  
|`pmBestFitEnabled`|执行最佳映射缺乏完全匹配 ANSI 字符集的 Unicode 字符。|  
|`pmBestFitDisabled`|不执行最佳的映射的 Unicode 字符。 在这种情况下，无法映射的所有字符将都替换为？。|  
|`pmBestFitMask`|保留。|  
|`pmThrowOnUnmappableCharUseAssem`|保留。|  
|`pmThrowOnUnmappableCharEnabled`|互操作封送处理程序遇到的无法映射字符时引发异常。|  
|`pmThrowOnUnmappableCharDisabled`|互操作封送处理程序遇到的无法映射字符时不会引发异常。|  
|`pmThrowOnUnmappableCharMask`|保留|  
|`pmSupportsLastError`|允许被调用方能够调用 Win32`SetLastError`从特性化方法返回之前的函数。|  
|`pmCallConvMask`|保留|  
|`pmCallConvWinapi`|使用默认平台调用约定。 例如，在 Windows 上默认值是`StdCall`以及它是 Windows CE.NET `Cdecl`。|  
|`pmCallConvCdecl`|使用`Cdecl`调用约定。 在这种情况下，调用方清理堆栈。 这样，与调用函数`varargs`（即，接受数目可变的参数的函数）。|  
|`pmCallConvStdcall`|使用`StdCall`调用约定。 在这种情况下，被调用方清理堆栈。 这是使用平台 invoke 调用非托管函数的默认约定。|  
|`pmCallConvThiscall`|使用`ThisCall`调用约定。 在这种情况下，第一个参数是`this`指针和存储在寄存器 ECX 中。 其他参数被推送到堆栈上。 `ThisCall`调用约定用于从非托管 DLL 导出的类上调用方法。|  
|`pmCallConvFastcall`|保留。|  
|`pmMaxValue`|保留。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
