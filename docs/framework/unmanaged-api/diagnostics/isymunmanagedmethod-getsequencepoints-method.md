---
title: ISymUnmanagedMethod::GetSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6b1e253fb7bf1a97f44e1eb05676fc356af9837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123703"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints 方法
获取在此方法内的所有序列点。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>参数  
 `cPoints`  
 [in]一个`ULONG32`，它接收的大小`offsets`， `documents`， `lines`， `columns`， `endLines`，和`endColumns`数组。  
  
 `pcPoints`  
 [out]一个指向`ULONG32`接收包含序列点所需的缓冲区的长度。  
  
 `offsets`  
 [in]一个数组，要在其中存储 Microsoft 中间语言 (MSIL) 偏移量从序列点方法的开头。  
  
 `documents`  
 [in]要在其中存储序列点所在的文档数组。  
  
 `lines`  
 [in]在其中存储序列点所在的文档中的行的数组。  
  
 `columns`  
 [in]在其中存储序列点所在的文档中的列的数组。  
  
 `endLines`  
 [in]序列点结束的文档中的行的数组。  
  
 `endColumns`  
 [in]序列点结束的文档中的列的数组。  
  
## <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym.idl CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedMethod 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
