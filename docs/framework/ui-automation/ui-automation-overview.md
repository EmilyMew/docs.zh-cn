---
title: UI 自动化概述
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 06cbc82f3636c4063b445a0ccbe871e0be1dd847
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134655"
---
# <a name="ui-automation-overview"></a>UI 自动化概述
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 是用于新的辅助功能框架[!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]，可在所有支持的操作系统上[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 以编程方式访问大多数[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]元素在桌面上，从而支持辅助技术产品，比如屏幕读取器提供了一些信息[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]向最终用户以及处理[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]而不借助标准输入。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 此外允许自动的测试脚本，以便与[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 不会启用由不同用户通过启动的进程之间的通信**以运行**命令。  
  
 UI 自动化客户端应用程序可在保证其将在多个框架上运行的情况下进行编写。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心掩盖位于 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]各组成部分之下的框架中的任何差异。 例如在 `Content` 视图中， [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 按钮的 `Caption` 属性、 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 按钮的 `ALT` 属性、HTML 图像的 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>属性全部映射到单个属性， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供了完整的功能[!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]， [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)]，和[!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)]。  
  
 UI 自动化提供程序通过内置的桥接服务提供了一些对 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] 客户端应用程序的支持。  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>提供程序和客户端  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 有四个主要组件下, 表中所示。  
  
|组件|描述|  
|---------------|-----------------|  
|提供程序 [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] （UIAutomationProvider.dll 和 UIAutomationTypes.dll）|一组接口定义，它们由 UI 自动化提供程序、提供关于 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 元素信息并响应编程输入的对象来实现。|  
|客户端 API（UIAutomationClient.dll 和 UIAutomationTypes.dll）|一组托管代码的类型，它们使 UI 自动化客户端应用程序可以获取有关 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 的信息，并将输入发送到控件。|  
|UiAutomationCore.dll|用于处理提供程序和客户端之间通信的基础代码（有时称为 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心）。|  
|UIAutomationClientsideProviders.dll|一组用于标准旧版本控件的 UI 自动化提供程序。 （[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 控件具有对 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的本机支持。）此支持自动提供给客户端应用程序。|  
  
 从软件开发人员的角度来看，有以下两种使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的方式：创建对自定义控件的支持（使用提供程序 API），创建使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心以与 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 元素通信的应用程序（使用客户端 API）。 具体取决于侧重点，你应参考文档中的其他部分。 你可在以下各节中进一步了解概念并获得实际操作知识。  
  
|节|行业专家|读者|  
|-------------|--------------------|--------------|  
|[UI 自动化基础知识](../../../docs/framework/ui-automation/index.md)（本节）|对概念的广泛概述。|全部。|  
|[托管代码的 UI 自动化提供程序](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|可帮助你使用提供程序 API 的概述和帮助主题。|控件开发人员。|  
|[托管代码的 UI 自动化客户端](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|可帮助你使用客户端 API 的概述和帮助主题。|客户端应用程序开发人员。|  
|[UI 自动化控件模式](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|有关提供程序应如何实现控件模式以及哪些功能可供客户端使用的信息。|全部。|  
|[UI 自动化文本模式](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|有关提供程序应如何实现 Text 控件模式以及哪些功能可供客户端使用的信息。|全部。|  
|[UI 自动化控件类型](../../../docs/framework/ui-automation/ui-automation-control-types.md)|有关不同控件类型支持的属性和控件模式的信息。|全部。|  
  
 下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间、包含这些命名空间的 DLL 以及使用它们的受众。  
  
|命名空间|被引用的 DLL|读者|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|UI 自动化客户端开发人员；用于查找 <xref:System.Windows.Automation.AutomationElement> 对象、注册 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件，并使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控件模式。|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]以外的其他框架的 UI 自动化提供程序的开发人员。|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]以外的其他框架的 UI 自动化提供程序的开发人员；用于实现 TextPattern 控件模式。|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]的 UI 自动化提供程序的开发人员。|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>UI 自动化模型  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 公开的每份[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]客户端应用程序作为<xref:System.Windows.Automation.AutomationElement>。 元素包含在树状结构，而桌面作为根元素。 客户端可将树的原始视图筛选为控件视图或内容视图。 应用程序还可以创建自定义视图。  
  
 <xref:System.Windows.Automation.AutomationElement> 对象公开的公共属性[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]它们所表示的元素。 这些属性之一则是控件类型，它将其基本外观和功能定义为单个可识别的实体：如按钮或复选框。  
  
 此外，元素公开向其控件类型提供特定属性的控件模式。 控件模式还公开方法，使客户端获取有关该元素的详细信息，并提供输入。  
  
> [!NOTE]
>  控件类型和控件模式之间并无一一对应关系。 一个控件模式可被多个控件类型支持，且一个控件可支持多个控件模式，两者均公开其行为的不同方面。 例如，组合框中至少具有两个控件模式：一个表示可展开和折叠的功能，另一个代表选择机制。 有关详细信息，请参阅 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 此外提供了如何通过事件的客户端应用程序的信息。 与 [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)]不同， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件不基于广播的机制。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 客户端注册特定的事件通知，并可以请求将特定[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]属性和控件模式信息传递给其事件处理程序。 此外， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件包含对引发它的元素的引用。 提供程序可以通过有选择地引发事件来提高性能，具体取决于任一客户端是否正在进行侦听。  
  
## <a name="see-also"></a>请参阅

- [UI 自动化树概述](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI 自动化控件模式概述](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI 自动化属性概述](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [UI 自动化事件概述](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [UI 自动化安全性概述](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
