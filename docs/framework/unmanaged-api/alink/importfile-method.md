---
title: ImportFile 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e48c6c3179ced167fdc39ae4df859f161727ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077246"
---
# <a name="importfile-method"></a>ImportFile 方法
导入程序集和未绑定的模块。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `pszFilename`  
 要导入文件的完全限定的名称。  
  
 `pszTargetName`  
 可用于重命名该文件并将其链接到该程序集的可选的输出文件名称。  
  
 `fSmartImport`  
 如果为 TRUE，则使用 ImportTypes 时，必须手动执行否则导入。  
  
 `pImportToken`  
 用于令牌存储唯一的文件 ID 的指针。 文件可以是程序集或文件。  
  
 `ppAssemblyScope`  
 接收指向[IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)。 如果该文件不是程序集，可以为 NULL。  
  
 `pdwCountOfScopes`  
 指向的文件和/或已导入的作用域的计数。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，返回，则为 S_OK。  
  
## <a name="requirements"></a>要求  
 需要 alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink 接口](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 接口](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
