---
title: ICorPublish::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116290"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses 方法
获取此计算机上运行的托管进程的枚举数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>参数  
 `Type`  
 值为[COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)枚举，用于指定要检索的进程的类型。 在最新版本，仅 COR_PUB_MANAGEDONLY 是有效的。  
  
 `ppIEnum`  
 指向的地址的指针[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)是进程的枚举器的实例。  
  
## <a name="remarks"></a>备注  
 枚举器的进程集合基于时正在运行的进程的快照`EnumProcesses`调用方法。 枚举器将不包括任何进程，终止之前或之后开始`EnumProcesses`调用。  
  
 `EnumProcesses`不止一次调用方法时可能会对此[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)实例以创建新的进程的最新集合。 后续调用将不会影响现有集合`EnumProcesses`方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorPub.idl CorPub.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorPublish 接口](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
