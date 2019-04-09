---
title: SetManifestFile 方法
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072423"
---
# <a name="setmanifestfile-method"></a>SetManifestFile 方法
可以指定或重置链接器在创建程序集时使用的清单文件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `pszFile`  
  
 Win32 资源的 blob 的内容放入清单文件的名称。  
  
## <a name="return-value"></a>返回值  
 如果该方法成功，返回，则为 S_OK。  
  
## <a name="remarks"></a>备注  
 询问 Win32ResBlob 前调用此操作。 值`pszFile`参数是其内容读取，并将其置于具有 ID 的 RT_MANIFEST Win32 资源的清单文件的名称。 通过使用 NULL 的参数调用时，将清除任何以前读取的清单。 这样，一个用于将链接器的状态重置为初始化时。  
  
## <a name="requirements"></a>要求  
 需要 aLink.h  
  
## <a name="see-also"></a>请参阅

- [IALink3 接口](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink 接口](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe（程序集链接器）](../../../../docs/framework/tools/al-exe-assembly-linker.md)
