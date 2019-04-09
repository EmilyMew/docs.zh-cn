---
title: ICLRRuntimeInfo::IsLoadable 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101583"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable 方法
指示与此接口关联的运行时是否可以加载到当前进程中，考虑到可能已加载到进程的其他运行时。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>参数  
 `pbLoadable`  
 [out]`true`如果此运行时可以加载到当前进程; 否则为`false`。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|该方法已成功完成。|  
|E_POINTER|`pbLoadable` 为 null。|  
  
## <a name="remarks"></a>备注  
 如果另一个运行时已加载到进程，并且与此接口关联的运行时可以加载过程中通过并行执行`pbLoadable`返回`true`。 如果两个运行时不能通过并行进程中运行，`pbLoadable`返回`false`。 例如，公共语言运行时 (CLR) 版本 4 可以运行与 CLR 2.0 版本在同一进程中并行或 CLR 版本 1.1。 但是，CLR 版本 1.1 和 CLR 版本 2.0 不能通过并行进程中运行。  
  
 如果没有运行时加载到进程，此方法始终返回`true`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MetaHost.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRRuntimeInfo 接口](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [宿主](../../../../docs/framework/unmanaged-api/hosting/index.md)
