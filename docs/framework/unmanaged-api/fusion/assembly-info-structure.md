---
title: ASSEMBLY_INFO 结构
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110872"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO 结构
包含有关在全局程序集缓存中注册程序集的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`cbAssemblyInfo`|以字节为单位，该结构的大小。 此字段保留为将来的扩展。|  
|`dwAssemblyFlags`|指示有关程序集的安装详细信息的标志。 支持以下值：<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 值，该值指示安装了该程序集。 .NET Framework 的当前版本始终设置`dwAssemblyFlags`为此值。<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 值，该值指示该程序集是常驻的有效负载。 .NET Framework 的当前版本永远不会设置`dwAssemblyFlags`为此值。|  
|`uliAssemblySizeInKB`|总大小，以千字节为单位，该程序集包含的文件。|  
|`pszCurrentAssemblyPathBuf`|指向包含到清单文件的当前路径的字符串缓冲区的指针。 路径必须以 null 字符结尾。|  
|`cchBuf`|包括 null 终止符的宽字符数的`pszCurrentAssemblyPathBuf`包含。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成结构](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [全局程序集缓存](../../../../docs/framework/app-domains/gac.md)
