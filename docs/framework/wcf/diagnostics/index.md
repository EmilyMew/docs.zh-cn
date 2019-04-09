---
title: 管理和诊断
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: 351d133215343e07e849ad1045eba601dd8cce56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092275"
---
# <a name="administration-and-diagnostics"></a>管理和诊断
Windows Communication Foundation (WCF) 提供了一套丰富的功能，可帮助你监视应用程序生存期的不同阶段。 例如，您可以在部署时使用配置来设置服务和客户端。 WCF 包含大量的性能计数器，可帮助您衡量应用程序的性能。 WCF 还公开在通过 WCF Windows Management Instrumentation (WMI) 提供程序的运行时服务的检测数据。 当应用程序出现错误或者开始错误操作时，可使用事件日志来了解是否有重大事件发生。 此外，还可以使用消息日志记录和跟踪来从头至尾查看应用程序中发生了哪些事件。 这些功能有助于开发人员和 IT 专业人员不正常时，WCF 应用程序进行故障排除。  
  
> [!NOTE]
>  如果收到没有具体详细信息的错误，则应启用`includeExceptionDetailInFaults`的属性[ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)配置元素。 这会指示 WCF 将异常详细信息发送到客户端，这样就可以检测许多常见的问题，而无需更高级的诊断。 有关详细信息，请参阅[Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF 提供的诊断功能  
 WCF 提供了以下诊断功能：  
  
-   端到端跟踪提供的检测数据可用于对应用程序进行故障排除而无需使用调试器。 WCF 输出跟踪进程的里程碑以及错误消息。 这可能包括打开通道工厂或者通过服务主机发送和接收消息。 可以为运行中的应用程序启用跟踪，以监视其进度。 有关详细信息，请参阅[跟踪](../../../../docs/framework/wcf/diagnostics/tracing/index.md)主题。 若要了解如何使用跟踪来调试应用程序，请参阅[解决您的应用程序中使用跟踪](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)主题。  
  
-   消息日志记录用于查看消息在传输前后的情况。 有关详细信息，请参阅[消息日志记录](../../../../docs/framework/wcf/diagnostics/message-logging.md)主题。  
  
-   事件跟踪针对所有主要问题将事件写入事件日志。 然后，可以使用事件查看器检查任何异常情况。 有关详细信息，请参阅[事件日志记录](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)主题。  
  
-   通过性能监视器公开的性能计数器可用于监视应用程序和系统的运行状况。 有关详细信息，请参阅[性能计数器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)主题。  
  
-   <xref:System.ServiceModel.Configuration> 命名空间用于加载配置文件和设置服务或客户端终结点。 如果必须将更新部署到很多计算机，可使用对象模型通过脚本对很多应用程序进行更改。 或者，可以使用[配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)编辑通过 GUI 向导的配置设置。 有关详细信息，请参阅[配置应用程序](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)主题。  
  
-   WMI 可用于查找哪些服务正在计算机上进行侦听，以及正在使用哪些绑定。 有关详细信息，请参阅[使用 Windows Management Instrumentation 进行诊断](../../../../docs/framework/wcf/diagnostics/wmi/index.md)主题。  
  
 WCF 还提供了许多 GUI 和命令行工具来使你更轻松地创建、 部署和管理 WCF 应用程序。 有关详细信息，请参阅[Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)。 例如，可以使用[配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)来创建和编辑 WCF 配置设置使用向导，而不直接编辑 XML。 此外可以使用[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)若要查看、 分组和筛选跟踪消息，以便可以诊断、 修复和验证 WCF 服务的问题。  
  
## <a name="see-also"></a>请参阅

- [配置应用程序](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [部署服务](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [关于异常的参考信息](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [事件日志记录](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [消息日志记录](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [服务跟踪查看器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel 注册工具](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [跟踪](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用 Windows Management Instrumentation 进行诊断](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [性能计数器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Windows Communication Foundation 工具](../../../../docs/framework/wcf/tools.md)
