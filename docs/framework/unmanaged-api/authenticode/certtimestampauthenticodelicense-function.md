---
title: CertTimestampAuthenticodeLicense 函数
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ac7cf92fb9c57491ff45e664513c0e82f22db9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111717"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense 函数
为验证码 XrML 许可证添加时间戳。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>参数  
 `pSignedLicenseBlob`  
 [in] 要添加时间戳的已签名验证码 XrML 许可证。 请参阅[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)结构。  
  
 `pwszTimestampURI`  
 [in] 时间戳服务器的 URI。  
  
 `pTimestampSignatureBlob`  
 [out] 指向 CRYPT_DATA_BLOB 的指针，用于接收 base64 编码的时间戳签名。 它是调用方负责释放`pTimestampSignatureBlob` -> `pbData`与`HepFree()`后使用。 请参阅[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)结构。  
  
## <a name="remarks"></a>备注  
 时间戳签名实际上是一条 PKCS #7 SignedData 消息，其内容是许可证签名中 SignatureValue 的二进制格式。 基本上，它充当许可证的副署。  
  
## <a name="return-value"></a>返回值  
 `S_OK` 如果函数成功。 否则，返回错误代码。  
  
## <a name="see-also"></a>请参阅

- [验证码](../../../../docs/framework/unmanaged-api/authenticode/index.md)
