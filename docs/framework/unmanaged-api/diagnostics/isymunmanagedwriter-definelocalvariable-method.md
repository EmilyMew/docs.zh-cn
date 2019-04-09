---
title: ISymUnmanagedWriter::DefineLocalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c561eb70f0e3d243984decfb39629601f8eeea37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125288"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable 方法
在当前词法范围内定义单个变量。 在范围内具有多个家庭的相同名称的变量，此方法可以调用多次。 在此情况下，但是，值`startOffset`和`endOffset`参数不能重叠。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>参数  
 `name`  
 [in]一个指向`WCHAR`，用于定义本地变量的名称。  
  
 `attributes`  
 [in]局部变量特性。  
  
 `cSig`  
 [in]一个`ULONG32`指示的大小，以字节为单位，`signature`缓冲区。  
  
 `signature`  
 [in]局部变量签名。  
  
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
 **标头：** CorSym.idl CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedWriter 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
