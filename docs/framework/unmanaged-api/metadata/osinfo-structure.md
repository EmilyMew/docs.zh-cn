---
title: OSINFO 结构
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096194"
---
# <a name="osinfo-structure"></a>OSINFO 结构
包含有关操作系统的程序集或模块的详细信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`dwOSPlatformId`|一个由 Microsoft Windows 平台函数定义的标识符值`GetVersionEx`。 支持以下值：<br /><br /> -VER_PLATFORM_WIN32s 或 0x0000，指定 Microsoft Windows 3.1。<br />-VER_PLATFORM_WIN32_WINDOWS 或从 0x0001，以指定 Windows 95 和 Windows 98 或继承自此它们的操作系统。<br />-VER_PLATFORM_WIN32_NT 或 0x0010，若要指定 Windows NT 或继承自它的操作系统。|  
|`dwOSMajorVersion`|操作系统主版本或 NULL 值，以指示任何版本。|  
|`dwOSMinorVersion`|操作系统次版本或 NULL 值，以指示任何版本。|  
  
## <a name="remarks"></a>备注  
 `OSINFO` 基于`OSVERSIONINFOEX`结构，它是 Microsoft Windows 平台函数调用中使用的`GetVersionEx`。 ASSEMBLYMETADATA 结构使用此结构以指示其操作系统的支持。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据结构](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
