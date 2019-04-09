---
title: IsFrameworkAssembly 函数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6c715183d3ae04130b729a9680335d65959836a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104060"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 函数
获取一个值，该值指示指定的程序集是否已托管。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>参数  
 `pwzAssemblyReference`  
 [in]要检查的程序集的名称。  
  
 `pbIsFrameworkAssembly`  
 [out]一个布尔值，该值指示是否为托管程序集。  
  
 `pwzFrameworkAssemblyIdentity`  
 [in]一个 uncanonicalized 的字符串，包含程序集的唯一标识。  
  
 `pccSize`  
 [输入] `pwzFrameworkAssemblyIdentity` 的大小。  
  
## <a name="remarks"></a>备注  
 `pwzAssemblyReference`参数是指向包含程序集名称的字符串。  
  
 如果此程序集是.NET Framework 的一部分`pbIsFrameworkAssembly`参数将包含一个布尔值为`true`。  
  
 如果命名的程序集不是.NET Framework 的一部分，或如果`pwzAssemblyReference`参数没有命名程序集`pbIsFrameworkAssembly`将包含一个布尔值为`false`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
## <a name="see-also"></a>请参阅

- [合成全局静态函数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
