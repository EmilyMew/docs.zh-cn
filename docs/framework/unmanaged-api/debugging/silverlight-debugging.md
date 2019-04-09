---
title: Silverlight 调试
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d20bc002e52c3c6a42b45c0d1c5d559e65dc52c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113693"
---
# <a name="silverlight-debugging"></a>Silverlight 调试
本部分中的主题描述了公共语言运行时 (CLR) 提供用于支持调试在 Windows 操作系统或在 Macintosh 平台上运行的基于 Silverlight 的应用程序的环境和接口。  
  
## <a name="in-this-section"></a>本节内容  
 [EnumerateCLRs 函数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 提供枚举进程中 CLR 的机制。  
  
 [CloseCLREnumeration 函数](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 关闭任何位于返回的句柄数组中的有效 CLR 继续启动事件[EnumerateCLRs 函数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)，并释放句柄和字符串路径数组的内存。  
  
 [CreateCoreClrDebugTarget 函数](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 创建进程和运行时枚举的远程目标连接。  
  
 [CreateCordbObject 函数](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 创建调试器界面，该界面提供用于实例化远程进程上托管的调试会话的功能。  
  
 [CreateVersionStringFromModule 函数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 从目标进程中的 CLR 路径创建版本字符串。  
  
 [CreateDebuggingInterfaceFromVersion 函数](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 接受从返回的 CLR 版本字符串[CreateVersionStringFromModule 函数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)函数，并返回相应的调试器接口。  
  
 [CoreClrDebugProcInfo 结构](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 表示在远程计算机上运行的进程。  
  
 [CoreClrDebugRuntimeInfo 结构](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 表示远程计算机进程中加载的 CLR 实例。  
  
 [GetStartupNotificationEvent 函数](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 创建或打开一个事件句柄，由在指定目标进程中加载的公共语言运行时 (CLR) 对其发出信号。  
  
 [ICoreClrDebugTarget 接口](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 创建进程和运行时枚举的远程目标连接。  
  
 [InitDbgTransportManager 函数](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 初始化传输管理器以连接到进程和运行时枚举的远程目标。  
  
 [ShutdownDbgTransportManager 函数](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 关闭用于远程目标计算机连接的传输管理器。  
  
## <a name="see-also"></a>请参阅

- [调试 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [调试全局静态函数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [调试枚举](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [调试结构](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
