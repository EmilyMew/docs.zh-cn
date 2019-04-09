---
title: IMetaDataEmit::DefineEvent 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48055103b49b4c61bb7561f2d4aa6c8daae07ae2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128903"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent 方法
使用指定的元数据签名中，创建一个事件的定义并获取该事件定义的标记。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a>参数  
 `td`  
 [in]目标类或接口的标记。 这可以是`mdTypeDef`或`mdTypeDefNil`令牌。  
  
 `szEvent`  
 [in]事件的名称。  
  
 `dwEventFlags`  
 [in]事件的标志。  
  
 `tkEventType`  
 [in]事件类标记。 这是`mdTypeDef`、 一个`mdTypeRef`，或`mdTokenNil`令牌。  
  
 `mdAddOn`  
 [in]用来订阅事件或为 null 的方法。  
  
 `mdRemoveOn`  
 [in]用于取消订阅事件，则为 null 的方法。  
  
 `mdFire`  
 [in]（由派生类） 用于引发事件的方法。  
  
 `rmdOtherMethods[]`  
 [in]有关其他方法与事件关联的标记的数组。 数组结尾`mdMethodDefNil`令牌。  
  
 `pmdEvent`  
 [out]分配到的事件的元数据标记。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
