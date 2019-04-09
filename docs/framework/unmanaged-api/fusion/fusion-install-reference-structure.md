---
title: FUSION_INSTALL_REFERENCE 结构
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110360"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE 结构
表示应用程序对应用程序已安装在全局程序集缓存中的程序集的引用。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`cbSize`|以字节为单位结构的大小。|  
|`dwFlags`|保留供将来的扩展。 此值必须为 0 （零）。|  
|`guidScheme`|会将引用添加的实体。 此字段可以具有以下值之一：<br /><br /> -FUSION_REFCOUNT_MSI_GUID:使用 Microsoft Windows Installer 安装的应用程序引用的程序集。 `szIdentifier`字段设置为`MSI`，并`szNonCanonicalData`字段设置为`Windows Installer`。 此方案用于 Windows 的并行程序集。<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID:将出现在应用程序引用的程序集**添加/删除程序**接口。 `szIdentifier`字段提供注册该应用程序使用的标记**添加/删除程序**接口。<br />-FUSION_REFCOUNT_FILEPATH_GUID:应用程序所表示的文件在文件系统中引用的程序集。 `szIdentifier`字段提供了此文件的路径。<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID:仅由不透明的字符串表示的应用程序引用的程序集。 `szIdentifier`字段提供了此不透明的字符串。 删除此值时在全局程序集缓存不会检查存在的不透明引用。<br />-FUSION_REFCOUNT_OSINSTALL_GUID:保留此值。|  
|`szIdentifier`|标识在全局程序集缓存中安装了程序集的应用程序的唯一字符串。 其值的值取决于`guidScheme`字段。|  
|`szNonCanonicalData`|一个字符串，仅会将引用添加的实体可以理解。 在全局程序集缓存将此字符串存储，但不使用它。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成结构](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [全局程序集缓存](../../../../docs/framework/app-domains/gac.md)
