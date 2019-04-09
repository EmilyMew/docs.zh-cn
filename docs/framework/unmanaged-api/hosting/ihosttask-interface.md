---
title: IHostTask 接口
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081497"
---
# <a name="ihosttask-interface"></a>IHostTask 接口
提供允许公共语言运行时 (CLR) 与要管理任务的主机进行通信的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alert 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|请求主机唤醒表示由当前的任务`IHostTask`的实例，因此，任务可以中止。|  
|[GetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|获取表示当前的任务的线程优先级别`IHostTask`实例。|  
|[Join 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|阻止，直到表示由当前的任务调用任务`IHostTask`实例完成后，指定的时间间隔结束，或[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)调用。|  
|[SetCLRTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|将相关联[ICLRTask 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)与当前实例`IHostTask`实例。|  
|[SetPriority 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|请求主机调整线程优先级级别表示由当前的任务`IHostTask`实例。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|请求主机将由当前的任务`IHostTask`实例从挂起状态到实时状态，可以在其中执行代码。|  
  
## <a name="remarks"></a>备注  
 CLR 调用由定义的方法`IHostTask`启动任务，来设置其线程优先级级别，依次类推。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRTask 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
