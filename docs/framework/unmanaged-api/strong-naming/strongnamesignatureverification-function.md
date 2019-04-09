---
title: StrongNameSignatureVerification 函数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c398663b84637d2551b0d94bd59b9e0994721ba5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124756"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 函数
获取一个值，该值指示提供的路径中的程序集清单是否包含根据指定标志验证的强名称签名。  
  
 此函数已弃用。 使用[iclrstrongname:: Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法相反。  
  
## <a name="syntax"></a>语法  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `wszFilePath`  
 [in]要验证的程序集的可移植可执行文件 （.dll 或.exe） 文件路径。  
  
 `dwInFlags`  
 [in]若要修改的验证行为的标志。 支持以下值：  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001)-强制实施验证，即使需要重写注册表设置。  
  
-   `SN_INFLAG_INSTALL` (0x00000002)-指定这是首次验证清单。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定缓存将允许仅对具有管理权限的用户的访问。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008)-指定程序集可以访问仅向当前用户。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010)-指定缓存将提供不保证其访问限制。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000)-保留以用于内部调试。  
  
 `pdwOutFlags`  
 [out]标志，该值指示是否已验证强名称签名。 支持以下值：  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值设置为`false`指定注册表设置使验证成功。  
  
## <a name="return-value"></a>返回值  
 `true` 如果验证成功;否则为`false`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** StrongName.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [StrongNameSignatureVerification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName 接口](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
