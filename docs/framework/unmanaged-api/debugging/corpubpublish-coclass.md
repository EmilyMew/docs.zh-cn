---
title: CorpubPublish Coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130528"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish Coclass
提供用于发布应用程序域和进程相关信息的接口。  
  
## <a name="syntax"></a>语法  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|[ICorPublish 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|提供用于发布有关进程和应用程序域的信息，这些进程中的方法。|  
|[ICorPublishAppDomain 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|表示，并提供有关在进程中的应用程序域的信息。|  
|[ICorPublishAppDomainEnum 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|提供遍历进程中当前存在的应用程序域的集合的方法。|  
|[ICorPublishProcess 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|表示在计算机运行的进程。|  
|[ICorPublishProcessEnum 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|提供遍历计算机运行的进程集合的方法。|  
  
## <a name="remarks"></a>备注  
 典型的发布方案是，开发人员想要调试在应用程序域的计算机运行的托管的代码。 宿主环境可能运行多个进程内的应用程序域。 开发人员想要使用图形用户界面或某些其他方法来列出所有的计算机，运行的进程并选取特定进程。 该列表应包括的所有应用程序域中运行托管的代码的进程。 然后，开发人员可以标识特定的应用程序域，并将调试器附加到该域。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorPub.idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
