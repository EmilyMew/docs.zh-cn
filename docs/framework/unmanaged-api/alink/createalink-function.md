---
title: CreateALink 函数
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b494b8b776f4cb0eb534233c5a03ab2d34a698ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115617"
---
# <a name="createalink-function"></a>CreateALink 函数
创建程序集链接器的实例并设置为指定接口的指针。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`riid`|一个程序集链接器接口的物理名称。|  
|`ppInterface`|在成功完成，包含一个指向的位置`riid`接口。|  
  
## <a name="requirements"></a>要求  
 **库**: alink.dll  
  
## <a name="see-also"></a>请参阅

- [Al.exe（程序集链接器）](../../../../docs/framework/tools/al-exe-assembly-linker.md)
