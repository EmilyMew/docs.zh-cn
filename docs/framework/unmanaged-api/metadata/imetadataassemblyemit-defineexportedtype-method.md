---
title: IMetaDataAssemblyEmit::DefineExportedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89fda72371f197efeeeef8f31ec396c334cfcb2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122026"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType 方法
创建包含指定导出类型的元数据的 `ExportedType` 结构，并返回关联的元数据标记。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>参数  
 `szName`  
 [in]要导出的类型的名称。 为版本 1.1 的公共语言运行时，导出的类型的名称必须与中给定的名称完全匹配`TypeDef`的类型。  
  
 `tkImplementation`  
 [in]指定导出的类型实现的位置标记。 有效的值和其关联的含义是：  
  
-   `mdFile` 类型是此程序集内的不同文件中实现的。  
  
-   `mdAssemblyRef` 类型是在不同的程序集中实现的。  
  
-   `mdExportedTYpe` 该类型嵌套在其他类型。  
  
-   `mdFileNil` 类型是在清单的同一个文件中并不是嵌套的类型。  
  
 `tkTypeDef`  
 [in]指定要导出的类型的元数据标记。 此值中输入`TypeDef`将实现类型，将只适用于该文件是在此程序集中的文件中的表。  
  
 `dwExportedTypeFlags`  
 [in]按位组合[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)定义导出的类型的属性设置的枚举值。  
  
 `pmdct`  
 [out]指向返回的元数据令牌，该值指示导出的类型的指针。  
  
## <a name="remarks"></a>备注  
 `ExportedType`必须为每种类型公开的此程序集和实现不包含清单的模块中定义元数据结构。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataAssemblyEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
