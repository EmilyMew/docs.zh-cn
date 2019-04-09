---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647c87b6f42b01922a385d502d72410af3140cd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095342"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
将绑定所有旧版公共语言运行时 (CLR) 版本 2 激活策略决策的当前运行时。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>返回值  
 此方法将返回以下特定的 Hresult:  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|绑定成功，或此运行时已被绑定为旧 CLR 版本 2 激活策略运行时。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|不同的运行时已绑定到旧的 CLR 版本 2 激活策略。|  
  
## <a name="remarks"></a>备注  
 如果当前运行时已绑定的所有旧 CLR 版本 2 激活策略决策 (例如，通过使用`useLegacyV2RuntimeActivationPolicy`特性，可以在[\<启动 > 元素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)配置文件中)，此方法不会返回错误结果;相反，则结果为 S_OK，只是因为它将该方法已成功绑定旧式激活策略。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MetaHost.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRRuntimeInfo 接口](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [宿主](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [\<启动 > 元素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
