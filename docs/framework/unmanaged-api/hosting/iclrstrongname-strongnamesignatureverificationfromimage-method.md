---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e09ac96a8803f41d78b532c9da67315e5dd6b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113732"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage 方法
验证已映射到内存的程序集对关联的公钥是否有效。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `pbBase`  
 [in]相对虚拟地址的映射的程序集清单。  
  
 `dwLength`  
 [in]以字节为单位，映射图像的大小。  
  
 `dwInFlags`  
 [in]影响验证行为的标志。 支持以下值：  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001)-强制实施验证，即使需要重写注册表设置。  
  
-   `SN_INFLAG_INSTALL` (0x00000002)-指定在此映像上执行第一次验证。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定缓存将允许仅对具有管理权限的用户的访问。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008)-指定程序集可以访问仅向当前用户。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010)-指定缓存将提供不保证其访问限制。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000)-保留以用于内部调试。  
  
 `pdwOutFlags`  
 [out]有关其他输出信息标志。 支持以下值：  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值设置为`false`指定注册表设置使验证成功。  
  
## <a name="return-value"></a>返回值  
 `S_OK` 如果成功，则完成的方法否则为指示失败的 HRESULT 值 (请参阅[常见的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)列表)。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MetaHost.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRStrongName 接口](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
