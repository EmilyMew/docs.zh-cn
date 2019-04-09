---
title: ICLRTaskManager 接口
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134649"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager 接口
提供了使宿主可以显式请求的公共语言运行时 (CLR) 的方法创建新的任务、 获取当前正在执行的任务，并设置地理语言和区域性的任务。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|显式请求 CLR 创建的新[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)实例。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|获取`ICLRTask`实例，它表示当前正在执行的任务。|  
|[GetCurrentTaskType 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|获取当前正在执行的任务的类型。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|通知 CLR 主机已修改当前正在执行的任务的区域设置标识符。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|通知公共语言运行时主机已修改当前正在执行的任务的用户界面区域设置标识符。|  
  
## <a name="remarks"></a>备注  
 在托管环境中运行每个任务宿主端有两个表示形式 (的实例[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) 和 CLR 侧 (实例[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md))。 在主机或 CLR 可以启动创建任务，但必须与相应的 CLR 端表示形式以确保在主机和关于此任务 CLR 之间的成功通信相关联的主机端表示形式。 必须创建和实例化操作系统线程上执行托管的代码之前的两个对象。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRTask 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
