---
title: MDAInfo 结构
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3be6f2b9454ed2f74d2cc6792cd9aaa2c25215db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104606"
---
# <a name="mdainfo-structure"></a>MDAInfo 结构
详细介绍`Event_MDAFired`触发托管调试助手 (MDA) 创建的事件。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`lpMDACaption`|当前的 MDA 的标题。 标题描述触发失败的`Event_MDAFired`事件。|  
|`lpMDAMessage`|提供当前 MDA 的输出消息。|  
  
## <a name="remarks"></a>备注  
 托管调试助手 (Mda) 是在运行时执行引擎中的调试辅助程序可与公共语言运行时 (CLR) 来执行任务，例如标识无效的条件结合或转储有关状态的其他信息引擎。 Mda 会生成有关则很难捕获的事件的 XML 消息。 它们将用于调试托管和非托管代码之间的转换非常有用。  
  
 在运行时激发的事件触发创建 MDA 时采用以下步骤：  
  
-   如果主机尚未注册[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)实例通过调用[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)接收通知`Event_MDAFired`事件，在运行时将继续进行其默认情况下，非托管的行为。  
  
-   如果主机已注册此事件的处理程序，运行时检查是否将调试程序附加到进程。 如果是，运行时将进入调试器。 当调试器会继续时，它调用到主机。 如果没有调试器已附加，则运行时调用`IActionOnCLREvent::OnEvent`，并将传递指向的指针`MDAInfo`实例作为`data`参数。  
  
 主机可以激活 Mda，MDA 激活时收到通知。 这会在主机重写默认行为并中止引发事件，以防止损坏进程状态的托管的线程的机会。 有关使用 Mda 的详细信息，请参阅[使用托管调试助手诊断错误](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.idl  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [承载结构](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [使用托管调试助手诊断错误](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
