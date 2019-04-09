---
title: ISymUnmanagedWriter2::DefineLocalVariable2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2caa9b48fc92a1b2e82f574d37d99758e19382c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133193"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 方法
在当前词法范围内定义单个变量。 在范围内具有多个家庭的相同名称的变量，此方法可以调用多次。 在此情况下，但是，值`startOffset`和`endOffset`参数不能重叠。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>参数  
 `name`  
 [in]本地变量名称。  
  
 `attributes`  
 [in]局部变量特性。  
  
 `sigToken`  
 [in]签名的元数据标记。  
  
 `addrKind`  
 [in]地址类型。  
  
 `addr1`  
 [in]参数规格的第一个地址。  
  
 `addr2`  
 [in]参数规格的第二个地址。  
  
 `addr3`  
 [in]参数规格的第三个地址。  
  
 `startOffset`  
 [in]变量的起始偏移量。 此参数可选。 如果该值为 0，则忽略此参数，并在整个范围内定义的变量。 如果它是一个非零值，该变量在当前作用域的偏移量之内。  
  
 `endOffset`  
 [in]变量的结束偏移量。 此参数可选。 如果该值为 0，则忽略此参数，并在整个范围内定义的变量。 如果它是一个非零值，该变量在当前作用域的偏移量之内。  
  
## <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL 或某些其他错误代码。  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym.idl  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedWriter2 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
