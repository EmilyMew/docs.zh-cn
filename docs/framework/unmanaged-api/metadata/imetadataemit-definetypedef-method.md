---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141799"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法
创建公共语言运行时类型的类型定义并获取该类型定义元数据标记。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>参数  
 `szTypeDef`  
 [in]以 unicode 格式的类型的名称。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性。 这是一个位掩码的`CoreTypeAttr`值。  
  
 `tkExtends`  
 [in]基类的标记。 它必须是`mdTypeDef`或`mdTypeRef`令牌。  
  
 `rtkImplements`  
 [in]指定此类或接口实现的接口的令牌的数组。  
  
 `ptd`  
 [out]`mdTypeDef`分配标记。  
  
## <a name="remarks"></a>备注  
 中的标志`dwTypeDefFlags`指定正在创建的类型是否为通用类型系统引用类型 （类或接口） 或通用类型系统值类型。  
  
 根据提供的参数，此方法，产生了负面影响，还可以创建`mdInterfaceImpl`记录为每个接口继承或由此类型实现的。 但是，此方法不返回其中的任何`mdInterfaceImpl`令牌。 如果客户端想要更高版本中添加或修改`mdInterfaceImpl`令牌，它必须使用`IMetaDataImport`接口来枚举它们。 如果你想要使用的 COM 语义`[default]`接口，您应作为中的第一个元素提供的默认接口`rtkImplements`; 在类上设置的自定义属性将指示类具有一个默认接口 (这始终被假定为第一次`mdInterfaceImpl`令牌声明的类)。  
  
 每个元素`rtkImplements`数组持有`mdTypeDef`或`mdTypeRef`令牌。 数组中的最后一个元素必须是`mdTokenNil`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
