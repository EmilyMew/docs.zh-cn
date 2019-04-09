---
title: LoadLibraryShim 函数
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32aee404891bfad1aed2abc9ad84e43bcd002df5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084565"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim 函数
加载指定的版本的.NET Framework 可再发行组件包中包含的 DLL。  
  
 此函数中不推荐[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 使用[iclrruntimeinfo:: Loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法相反。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>参数  
 `szDllName`  
 [in]的以零结尾的字符串表示要从.NET Framework 库加载的 DLL 的名称。  
  
 `szVersion`  
 [in]的以零结尾的字符串表示要加载的 dll 版本。 如果`szVersion`是 null，选择用于加载是指定早于版本 4 的 DLL 的最新版本的版本。 如果所有版本等于或大于版本 4 则将都忽略，即`szVersion`为 null，并且如果不安装任何版本低于版本 4，则无法加载 DLL。 这是为了确保该安装[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不会影响现有应用程序或组件。 请参阅文章[进程内并行和迁移快速启动](https://go.microsoft.com/fwlink/?LinkId=200329)CLR 团队博客中。  
  
 `pvReserved`  
 留待将来使用。  
  
 `phModDll`  
 [out]指向模块的句柄的指针。  
  
## <a name="return-value"></a>返回值  
 此方法返回标准的组件对象模型 (COM) 错误代码，定义在 WinError.h，除了以下值。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|S_OK|该方法已成功完成。|  
|CLR_E_SHIM_RUNTIMELOAD|正在加载`szDllName`需要在加载公共语言运行时 (CLR)，并在 CLR 的必要版本无法加载。|  
  
## <a name="remarks"></a>备注  
 此函数用于加载.NET Framework 可再发行组件包中包含的 Dll。 它将不加载用户生成的 Dll。  
  
> [!NOTE]
>  从.NET Framework 2.0 版开始，将加载 Fusion.dll 导致要加载的 CLR。 这是因为在 Fusion.dll 函数现在是由运行时提供其实现的包装器。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [弃用的 CLR 承载函数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
