---
title: _CorValidateImage 函数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111171"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage 函数
验证托管的模块映像，并已加载后通知操作系统加载程序。  
  
## <a name="syntax"></a>语法  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>参数  
 `ImageBase`  
 [in]指向要作为验证的图像的起始位置的托管代码。 该映像必须已加载到内存中。  
  
 `FileName`  
 [in]图像的文件名。  
  
## <a name="return-value"></a>返回值  
 此函数返回的标准值`E_INVALIDARG`， `E_OUTOFMEMORY`， `E_UNEXPECTED`，和`E_FAIL`，以及以下值。  
  
|返回值|描述|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|映像是无效的。 此值具有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|映像是有效的。 此值具有 HRESULT 0x00000000L。|  
  
## <a name="remarks"></a>备注  
 在 Windows XP 和更高版本中，操作系统加载程序通过检查通用对象文件格式 (COFF) 标头中的 COM 描述符目录位检查托管模块。 一个设置位指示托管的模块。 如果加载程序检测到托管的模块时，它将加载 MsCorEE.dll 并调用`_CorValidateImage`，该文件将执行以下操作：  
  
-   确认该图像是有效的托管的模块。  
  
-   在图中的入口点更改为公共语言运行时 (CLR) 中的入口点。  
  
-   对于 64 位版本的 Windows，修改在内存中是通过将其从 PE32 转换为 PE32 + 格式的图像。  
  
-   返回到加载程序加载托管的模块映像时。  
  
 对于可执行映像，操作系统加载程序然后调用[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函数，而不考虑可执行文件中指定的入口点。 对于 DLL 程序集图像加载程序调用[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函数。  
  
 `_CorExeMain` 或`_CorDllMain`将执行以下操作：  
  
-   初始化 CLR。  
  
-   查找程序集的 CLR 标头中的托管的入口点。  
  
-   开始执行。  
  
 加载程序调用[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函数时托管模块映像都会被卸载。 但是，此函数不执行任何操作;它只是返回。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据全局静态函数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
