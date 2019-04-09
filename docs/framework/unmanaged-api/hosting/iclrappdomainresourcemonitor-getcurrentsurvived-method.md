---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141539"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
获取上次的完整、 阻碍性垃圾回收后保留下来并由当前的应用程序域引用的字节数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>参数  
 `dwAppDomainId`  
 [in]请求的应用程序域的 ID。  
  
 `pAppDomainBytesSurvived`  
 [out]指向最后一个垃圾回收后仍存在于此应用程序域所持有的字节数的指针。 完整回收之后，此数字是准确和完整。 暂时回收之后，此数字是可能不完整。 此参数可以为 `null`。  
  
 `pRuntimeBytesSurvived`  
 [out]指向最后一个垃圾回收后保留的字节总数的指针。 完整回收之后，此数字表示托管堆中保留的字节数。 暂时回收之后，此数字表示暂时生成中实时保留的字节数。 此参数可以为 `null`。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|该方法已成功完成。|  
|COR_E_APPDOMAINUNLOADED|应用程序域已被卸载，或不存在。|  
  
## <a name="remarks"></a>备注  
 仅在完整、 阻碍性垃圾回收; 后更新统计信息也就是说，其中包括所有的生成和停止应用程序，同时集合的集合时发生。 例如，<xref:System.GC.Collect?displayProperty=nameWithType>方法重载执行完整、 阻碍性回收。 并发垃圾回收在后台发生，并不会阻止应用程序。  
  
 `GetCurrentSurvived`方法是托管的非托管等效项<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>属性。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MetaHost.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRAppDomainResourceMonitor 接口](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [应用程序域资源监控](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [宿主](../../../../docs/framework/unmanaged-api/hosting/index.md)
