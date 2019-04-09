---
title: IMetaDataImport::ResolveTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f929e6b338d4fd48b2a6ef9588523377e0dd8faa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096057"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef 方法
解析<xref:System.Type>指定的 TypeRef 标记所表示的引用。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>参数  
 `tr`  
 [in]要返回的被引用的类型信息的 TypeRef 元数据标记。  
  
 `riid`  
 [in]若要在中返回的接口的 IID `ppIScope`。 通常情况下，这将是 IID_IMetaDataImport。  
  
 `ppIScope`  
 [out]一个要在其中定义被引用的类型在模块作用域的接口。  
  
 `ptd`  
 [out]指向表示被引用的类型的 TypeDef 标记的指针。  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  如果加载多个应用程序域，则不使用此方法。 该方法不会接受应用程序域边界。 如果加载了多个版本的程序集，并且它们包含具有相同的命名空间的相同类型，该方法将返回它找到的第一个类型在模块作用域。  
  
 `ResolveTypeRef`方法搜索的其他模块中的类型定义。 如果找到该类型定义，则`ResolveTypeRef`返回一个指向该模块作用域，以及类型的 TypeDef 标记接口。  
  
 如果要将解析的类型引用具有 AssemblyRef，解析范围`ResolveTypeRef`方法搜索匹配项仅在已打开与调用的元数据作用域中[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法或[imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法。 这是因为`ResolveTypeRef`无法确定从磁盘上或位于全局程序集缓存程序集的存储位置的 AssemblyRef 范围。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
