---
title: IMetaDataImport::GetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c61931f5f6a4bbbf66446d68b0d1b2d1df958a66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137912"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps 方法
获取与指定的 MethodDef 标记引用的方法关联的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `mb`  
 [in]表示要返回的元数据的方法的 MethodDef 标记。  
  
 `pClass`  
 [out]指向表示实现方法的类型的 TypeDef 标记的指针。  
  
 `szMethod`  
 [out]指向方法的名称的缓冲区的指针。  
  
 `cchMethod`  
 [in]请求的大小`szMethod`。  
  
 `pchMethod`  
 [out]一个指向宽字符为单位的大小`szMethod`，或发生截断时，实际方法名称中的宽字符数。  
  
 `pdwAttr`  
 [out]一个指向与方法关联的任何标志。  
  
 `ppvSigBlob`  
 [out]指向方法的二进制元数据签名的指针。  
  
 `pcbSigBlob`  
 [out]指向以字节为单位的大小的`ppvSigBlob`。  
  
 `pulCodeRVA`  
 [out]指向方法的相对虚拟地址的指针。  
  
 `pdwImplFlags`  
 [out]指向方法的任何实现标志的指针。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
