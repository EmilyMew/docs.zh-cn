---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6e4be2e05c573ec93cc23c8dd6eccc834b8b848
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136495"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls 方法
枚举指定实现的所有接口`TypeDef`。 
  
## <a name="syntax"></a>语法  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>参数  
 `phEnum`  
 [in、 out]一个指向枚举器。  
  
 `td`  
 [in]表示接口实现的 MethodDef 标记是要枚举的 TypeDef 标记。  
  
 `rImpls`  
 [out]用于存储 MethodDef 标记的数组。  
  
 `cMax`  
 [in] `rImpls` 数组的最大大小。  
  
 `pcImpls`  
 [out]令牌中返回的实际数目`rImpls`。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` 已成功返回。|  
|`S_FALSE`|没有要枚举的 MethodDef 标记。 在这种情况下，`pcImpls`设置为零。|  

## <a name="remarks"></a>备注

此枚举返回的集合`mdInterfaceImpl`令牌，以实现由指定的每个接口进行`TypeDef`。 指定接口的顺序返回接口标记 (通过`DefineTypeDef`或`SetTypeDefProps`)。 所返回的属性`mdInterfaceImpl`可以使用查询令牌[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)。
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
