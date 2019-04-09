---
title: IMetaDataImport::GetInterfaceImplProps 方法
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76e2ebbd47a5e36a722fce33ba67d7efb4db8675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115929"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps 方法
获取一个指针指向的元数据令牌<xref:System.Type>实现指定的方法和接口，其用于声明该方法。
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>参数  
 `iiImpl`  
 [in]表示此方法返回的类和接口令牌的元数据标记。  
  
 `pClass`  
 [out]表示实现方法的类的元数据标记。  
  
 `ptkIface`  
 [out]表示定义实现的方法的接口的元数据标记。  

## <a name="remarks"></a>备注

 获取值以供`iImpl`通过调用[EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md)方法。
 
 例如，假设类具有`mdTypeDef`令牌 0x02000007 的值，它实现的类型具有令牌的三个接口： 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

从概念上讲，此信息存储到作为接口实现表：

| 行号 | 类令牌 | 接口令牌 |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

请注意，该令牌是一个 4 字节值：

- 较低的 3 个字节存储的行号，或 RID。
- 高位字节包含标记类型 – 为 0x09 `mdtInterfaceImpl`。

`GetInterfaceImplProps` 返回信息保存在行中提供的令牌`iImpl`参数。 
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
