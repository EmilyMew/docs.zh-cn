---
title: StrongNameKeyGenEx 函数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af75a645b11325b96740807f9a3df65f5a676026
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120837"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx 函数
生成新公钥/私钥对与指定的密钥大小，用于强名称。  
  
 此函数已弃用。 使用[iclrstrongname:: Strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)方法相反。  
  
## <a name="syntax"></a>语法  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>参数  
 `wszKeyContainer`  
 [in]请求的密钥容器名称。 `wszKeyContainer` 必须为非空字符串，或空值，以生成一个临时名称。  
  
 `dwFlags`  
 [in]指定是否保留注册密钥。 支持以下值：  
  
-   0x00000000-时使用`wszKeyContainer`为 null 以生成一个临时密钥容器名称。  
  
-   0x00000001 (`SN_LEAVE_KEY`)-指定应保持注册密钥。  
  
 `dwKeySize`  
 [in]请求的密钥，以位为单位的大小。  
  
 `ppbKeyBlob`  
 [out]返回的公共/专用密钥对。  
  
 `pcbKeyBlob`  
 [out]大小，以字节为单位的`ppbKeyBlob`。  
  
## <a name="return-value"></a>返回值  
 `true` 在成功完成;否则为`false`。  
  
## <a name="remarks"></a>备注  
 .NET framework 1.0 和 1.1 版需要`dwKeySize`1024 位使用强名称; 程序集进行签名的版本 2.0 添加为 2048年位密钥的支持。  
  
 正在检索密钥后，应调用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函数，以释放已分配的内存。  
  
 如果`StrongNameKeyGenEx`函数不成功完成，则调用[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函数检索最后一个生成的错误。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** StrongName.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [StrongNameKeyGenEx 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen 方法](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName 接口](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
