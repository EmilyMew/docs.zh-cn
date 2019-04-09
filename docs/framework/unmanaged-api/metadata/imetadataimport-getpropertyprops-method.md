---
title: IMetaDataImport::GetPropertyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08bd5beeb9fab1cd5b703c3afc4e82aaf71dbbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122598"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps 方法
获取表示指定的标记的属性的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a>参数  
 `prop`  
 [in]表示要返回的元数据的属性的标记。  
  
 `pClass`  
 [out]指向表示实现属性的类型的 TypeDef 标记的指针。  
  
 `szProperty`  
 [out]用于保存的属性名称的缓冲区。  
  
 `cchProperty`  
 [in]在宽字符为单位的大小`szProperty`。  
  
 `pchProperty`  
 [out]在中返回的宽字符数`szProperty`。  
  
 `pdwPropFlags`  
 [out]指向应用于属性的任何属性标志的指针。 此值是从一个位掩码[CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)枚举。  
  
 `ppvSig`  
 [out]一个指向该属性的元数据签名。  
  
 `pbSig`  
 [out]在返回的字节数`ppvSig`。  
  
 `pdwCPlusTypeFlag`  
 [out]一个指定类型的常量，它是属性的默认值的标志。 此值是从 CorElementType 枚举。  
  
 `ppDefaultValue`  
 [out]指向存储此属性的默认值的字节的指针。  
  
 `pcchDefaultValue`  
 [out]在宽字符为单位的大小`ppDefaultValue`，如果`pdwCPlusTypeFlag`是 ELEMENT_TYPE_STRING; 否则，此值不是相关。 在这种情况下，时长`ppDefaultValue`从指定的类型推断`pdwCPlusTypeFlag`。  
  
 `pmdSetter`  
 [out]指向表示属性的 set 访问器方法的 MethodDef 标记的指针。  
  
 `pmdGetter`  
 [out]指向表示属性的 get 访问器方法的 MethodDef 标记的指针。  
  
 `rmdOtherMethod`  
 [out]一个表示与属性关联的其他方法的 MethodDef 标记的数组。  
  
 `cMax`  
 [in] `rmdOtherMethod` 数组的最大大小。 如果未提供足够大以保存所有方法的数组，则跳过而不发出警告。  
  
 `pcOtherMethod`  
 [out]在中返回的 MethodDef 标记数`rmdOtherMethod`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
