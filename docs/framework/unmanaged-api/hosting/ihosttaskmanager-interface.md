---
title: IHostTaskManager 接口
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da30e75bf4a58e66bb0dd8210368b162cf14c3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091260"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager 接口
提供允许公共语言运行时 (CLR) 用于通过而不是使用标准操作系统线程或纤程函数主机的任务的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|通知宿主托管代码进入不能在其中中止当前任务的周期。|  
|[BeginThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|通知宿主托管代码进入在其中将当前的任务必须不移动到另一个操作系统线程的周期。|  
|[CallNeedsHostHook 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|使宿主能够指定公共语言运行时是否可以内联指定调用非托管函数。|  
|[CreateTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|主机创建新的任务的请求。|  
|[EndDelayAbort 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|通知宿主托管代码正在退出在其中不必须中止当前任务，周期遵循早期调用`BeginDelayAbort`。|  
|[EndThreadAffinity 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|通知宿主托管代码正在退出不能在其当前任务移动到另一个操作系统线程，周期遵循早期调用`BeginThreadAffinity`。|  
|[EnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|通知主机，对非托管方法的调用以便为平台调用方法，将执行控制返回到 CLR。|  
|[GetCurrentTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|获取从其进行此调用的操作系统线程当前正在执行的任务的接口指针。|  
|[GetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|获取的堆栈空间后的堆栈操作完成后，可保证，但在关闭进程之前的量。|  
|[LeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|通知宿主托管代码将要对非托管函数进行调用。|  
|[ReverseEnterRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|通知主机正在到公共语言运行时 (CLR) 从非托管代码进行调用。|  
|[ReverseLeaveRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|通知主机控制正在离开 CLR 并输入从托管代码调用非托管的函数。|  
|[SetCLRTaskManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|为宿主提供的接口指针到[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)由 CLR 实现的实例。|  
|[SetLocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|通知宿主 CLR 已更改了当前任务中的区域设置。|  
|[SetStackGuarantee 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|保留以仅供内部使用。|  
|[SetUILocale 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|通知主机用户界面区域设置已在当前任务。|  
|[Sleep 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|通知主机当前任务即将进入睡眠状态。|  
|[SwitchToTask 方法](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|通知主机应切换当前任务。|  
  
## <a name="remarks"></a>备注  
 `IHostTaskManager` 使 CLR 能够创建和管理任务，以提供挂钩，以便主机控件从托管代码转换到非托管代码，反之亦然时, 执行的操作并指定特定的操作，主机可以并且不能创建在代码执行过程。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRTask 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 接口](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
