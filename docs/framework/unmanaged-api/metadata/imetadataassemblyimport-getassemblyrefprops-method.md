---
title: IMetaDataAssemblyImport::GetAssemblyRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089778"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps 方法
获取具有指定的元数据签名的程序集引用的属性集。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `mdar`  
 [in]`mdAssemblyRef`表示要为其获取属性的程序集引用的元数据标记。  
  
 `ppbPublicKeyOrToken`  
 [out]公钥或元数据标记的指针。  
  
 `pcbPublicKeyOrToken`  
 [out]返回公钥或标记中的字节数。  
  
 `szName`  
 [out]程序集的简单名称。  
  
 `cchName`  
 [in]大小，以宽字符为单位的`szName`。  
  
 `pchName`  
 [out]指向的宽字符中实际返回数的`szName`。  
  
 `pMetaData`  
 [out]指向包含程序集元数据的 ASSEMBLYMETADATA 结构的指针。  
  
 `ppbHashValue`  
 [out]指向哈希值的指针。 这是使用 sha-1 算法，哈希`PublicKey`除非 arfFullOriginator 标记所引用的程序集的属性[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)枚举设置。  
  
 `pcbHashValue`  
 [out]中返回的哈希值的宽字符数。  
  
 `pdwAssemblyRefFlags`  
 [out]指向描述应用于程序集的元数据的标志的指针。 标志值是一个或多个组合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。  
  
## <a name="return-value"></a>返回值  
 此方法返回时如果它成功，则为 S_OK否则，它返回一个在 Winerror.h 标头文件中定义的错误代码。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
