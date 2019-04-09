---
title: GetRequestedRuntimeVersionForCLSID 函数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081887"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 函数
获取相应的公共语言运行时 (CLR) 版本信息，为具有指定类`CLSID`。  
  
 此函数中不推荐[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `rclsid`  
 [in] `CLSID`的组件。  
  
 `pVersion`  
 [out] 包含成功完成后的版本字符串的缓冲区。  
  
 `cchBuffer`  
 [in] 大小，以宽字符为单位的`pVersion`缓冲区。  
  
 `dwLength`  
 [out]返回的缓冲区长度 （字节）。  
  
 `dwResolutionFlags`  
 [in] CLSID_RESOLUTION_FLAGS 值之一。 支持以下值：  
  
-   CLSID_RESOLUTION_DEFAULT:(0x0) 指定应使用默认互操作行为。  
  
-   CLSID_RESOLUTION_REGISTERED:(0x1) 指定应搜索注册表和应应用填充程序策略。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|该函数返回成功。|  
|E_INVALIDARG|参数之一具有无效的类型或格式。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`缓冲区不是大到足以保留完整版本字符串。|  
|REGDB_E_CLASSNOTREG|没有与指定注册类`CLSID`。|  
|E_POINTER|`dwLength` 为 null，或`cchBuffer`足够大以保存的版本字符串，但`pVersion`为 null。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [弃用的 CLR 承载函数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
