---
title: GetVersionFromProcess 函数
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 452104939acf5de7bb151cba00d65fb6631c98d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124080"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 函数
获取与指定的进程句柄关联的公共语言运行时 (CLR) 的版本号。  
  
 此函数中不推荐[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>参数  
 `hProcess`  
 [in]进程的句柄。  
  
 `pVersion`  
 [out]包含该方法成功完成后的版本字符串的缓冲区。  
  
 `cchBuffer`  
 [in]版本缓冲区的长度。  
  
 `pdwLength`  
 [out]指向的版本号字符串长度的指针。  
  
## <a name="return-value"></a>返回值  
 此方法返回标准的组件对象模型 (COM) 错误代码，定义在 WinError.h，除了以下值。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|S_OK|该方法已成功完成。|  
|E_INVALIDARG|`pVersion` 为 null 和`cchBuffer`不为 null，反之亦然。<br /><br /> 或<br /><br /> `hProcess` 不是有效的句柄到的进程。<br /><br /> 或<br /><br /> 未加载 CLR。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` 为 null 或小于版本字符串的长度。|  
|E_NOTIMPL|此方法不是 Microsoft Windows 95、 Microsoft Windows 98 或 Microsoft Windows Millennium Edition 操作系统上可用。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetRequestedRuntimeInfo 函数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 函数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [弃用的 CLR 承载函数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
