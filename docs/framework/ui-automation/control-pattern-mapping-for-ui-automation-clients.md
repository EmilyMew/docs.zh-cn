---
title: UI 自动化客户端的控件模式映射
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 829df66f49d5df5f5c8cf8d2b6cfa74f0a2172dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101128"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI 自动化客户端的控件模式映射
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主题列出了控件类型及其关联的控件模式。  
  
 下表将控件模式整理为以下类别：  
  
-   支持。 控件必须支持此控件模式。  
  
-   有条件支持。 控件可能支持此控件模式，具体取决于控件的状态。  
  
-   不支持。 控件不支持此控件模式；自定义控件可能支持此控件模式。  
  
> [!NOTE]
>  某些控件有条件支持一些控件模式，具体取决于控件的功能。 例如，菜单项控件有条件支持 <xref:System.Windows.Automation.InvokePattern>、 <xref:System.Windows.Automation.ExpandCollapsePattern>、 <xref:System.Windows.Automation.TogglePattern>或 <xref:System.Windows.Automation.SelectionItemPattern> 控件模式，具体取决于其菜单控件中的功能。  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>客户端的 UI 自动化控件模式  
  
|控件类型|支持|有条件支持|不支持|  
|------------------|---------------|-------------------------|-------------------|  
|Button|None|调用、切换、展开折叠|None|  
|Calendar|网格、表|选择、滚动|“值”|  
|复选框|切换|None|None|  
|组合框|展开/折叠|选择、值|Scroll|  
|数据网格|Grid|滚动、选择、表|None|  
|数据项|选择项|展开折叠、网格项、滚动项、表、切换、值|None|  
|Document|Text|滚动、值|None|  
|Edit|None|文本、范围值、值|None|  
|Group|None|展开/折叠|None|  
|Header|None|Transform|None|  
|标头项|None|转换、调用|None|  
|超链接|调用|“值”|None|  
|图像|None|网格项、表项|调用、选择项|  
|列表|None|网格、多个视图、滚动、选择|表|  
|列表项|选择项|展开折叠、网格项、调用、滚动项、切换、值|None|  
|菜单|None|None|None|  
|菜单栏|None|展开折叠、停靠、转换|None|  
|菜单项|None|展开折叠、调用、选择项、切换|None|  
|Pane|None|停靠。 滚动、转换|窗口|  
|进度栏|None|范围值、值|None|  
|单选按钮|选择项|None|切换|  
|滚动条|None|范围值|Scroll|  
|Separator|None|None|None|  
|Slider|None|范围值、选择、值|None|  
|Spinner|None|范围值、选择、值|None|  
|拆分按钮|调用、展开折叠|None|None|  
|状态栏|None|Grid|None|  
|Tab|选择|Scroll|None|  
|选项卡项|选择项|None|调用|  
|表|网格、网格项、表、表项|None|None|  
|Text|None|网格项、表项、文本|“值”|  
|Thumb|Transform|None|None|  
|标题栏|None|None|None|  
|工具栏|None|停靠、展开折叠、转换|None|  
|工具提示|None|文本、窗口|None|  
|树|None|滚动、选择|None|  
|树项|展开/折叠|调用，滚动项、选择项、切换|None|  
|窗口|转换、窗口|停靠|None|  
  
> [!NOTE]
>  如果控件类型没有可列出的受支持的控件模式，但具有一个或多个有条件支持的控件模式，则将始终支持这些有条件控件模式之一。  
  
## <a name="see-also"></a>请参阅

- [UI 自动化概述](../../../docs/framework/ui-automation/ui-automation-overview.md)
