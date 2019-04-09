---
title: UI 自动化和 Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 29a6b897115c5f2f3ae8d7e4ec708be59dc0d85b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115331"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI 自动化和 Microsoft Active Accessibility
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] 是使应用程序可以访问的早期解决方案。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 是用于新的辅助功能模型[!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]和适用于以下的辅助技术产品的需求和自动测试工具。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 通过提供很多改进[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]。  
  
 本主题包含了 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的主要功能并解释了这些功能与 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]的不同之处。  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>编程语言  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 基于[!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)]具有双重接口支持，因此 C/c + + 中可编程[!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]，和脚本语言。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] （包括适用于标准控件的客户端提供程序库） 编写托管代码中，UI 自动化客户端应用程序轻松进行编程使用 C# 或 Visual Basic.NET。 作为接口实现的 UI 自动化提供程序可以用托管代码或 C/C++ 编写。  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation 中的支持  
 Windows Presentation Foundation (WPF) 是用于创建用户界面的新模型。 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 元素不包含对本机支持[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; 但是，它们支持[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，其中包括桥接支持[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]客户端。 只有专门为 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 编写的客户端才可以充分利用 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]的辅助功能，例如对文本的丰富支持。  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>服务器和客户端  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中，服务器和客户端主要通过服务器的 `IAccessible`实现进行直接通信。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，核心服务位于服务器（称为提供程序）和客户端之间。 核心服务对由提供程序实现的接口进行调用并提供其他服务，例如，为元素生成唯一的运行时标识符。 客户端应用程序使用库函数来调用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 服务。  
  
 UI 自动化提供程序可以将信息提供给 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 客户端，而 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器可以将信息提供给 UI 自动化客户端应用程序。 但是，由于 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 没有公开同 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]一样多的信息，因此两个模型并不完全兼容。  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>UI 元素  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 提供了[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]元素为`IAccessible`接口或子标识符的形式。 很难比较两个 `IAccessible`指针来确定它们是否引用同一元素。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，每个元素都表示为一个 <xref:System.Windows.Automation.AutomationElement> 对象。 可通过使用相等运算符或 <xref:System.Windows.Automation.AutomationElement.Equals%2A> 方法完成比较，这两种方法比较的都是元素的唯一运行时标识符。  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>树视图和导航  
 屏幕上的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 元素可以被视为树状结构，桌面作为根、应用程序窗口作为直接子项，而应用程序中的元素作为继承子项。  
  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中，许多与最终用户不相关的自动化元素都公开在树中。 客户端应用程序需要查看所有元素以确定哪些元素是有意义的。  
  
 UI 自动化客户端应用程序通过筛选视图查看 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。 该视图仅包含相关元素：向用户提供信息或实现交互的元素。 还提供了只包含控件元素和只包含内容元素的预定义视图；除此之外，应用程序还可以定义自定义视图。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 描述的任务，简化了[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]到用户，并帮助用户与应用程序进行交互。  
  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中元素之间的导航可以是空间导航（例如，移动到存在于屏幕左侧的元素）、逻辑导航（例如，移动到下一菜单项或对话框中 Tab 键顺序的下一项）或分层导航（例如，移动到容器中的第一个子级，或者从子级移动到其父级）。 分层导航非常复杂，因为子元素并不总是实现 `IAccessible`的对象。  
  
 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中，所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 元素都是支持相同基本功能的 <xref:System.Windows.Automation.AutomationElement> 对象。 （从提供程序的角度来看，它们是实现继承自 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>的接口的对象。）导航主要是分层导航：从父级到子级，以及从同级到下一个同级。 （同级之间的导航具有一个逻辑元素，因为它可能遵照的是 Tab 键顺序。）通过使用 <xref:System.Windows.Automation.TreeWalker>类，你可以使用树的任何筛选视图从任何起点进行导航。 你还可以通过使用 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>和 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 导航到特定的子级或继承项；例如，很容易检索对话框中支持指定控件模式的所有元素。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中的导航比 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 中的导航更加一致。 某些元素（例如下拉列表和弹出窗口）在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 树中出现两次，且从它们进行导航可能出现意外结果。 其实就是无法对 rebar 控件正确实现 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 能够重排根目录并重新定位，以便在窗口的层次结构树中任何位置放置一个元素。  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>角色和控件类型  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 使用`accRole`属性 (`IAccessible::get_actRole`) 来检索元素的角色中的说明[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]，如 ROLE_SYSTEM_SLIDER 或 ROLE_SYSTEM_MENUITEM。 元素的角色是确定其可用功能的主要线索。 通过使用固定的方法（如 `IAccessible::accSelect` 和 `IAccessible::accDoDefaultAction`）可实现与控件的交互。 客户端应用程序和 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]之间的交互仅限于可通过 `IAccessible` 完成的交互。  
  
 与此相反， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 很大程度上会将该元素的控件类型（由 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 属性描述）从其预期的功能分离。 功能由通过实现其特殊化接口的提供程序支持的控件模式来确定。 可以结合控件模式来描述特定 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 元素支持的完整功能集。 某些提供程序需要支持特定的控件模式；例如，复选框的提供程序必须支持 Toggle 控件模式。 其他提供程序需要支持一个或多个控件模式集；例如，一个按钮必须支持 Toggle 或 Invoke。 还有一些提供程序完全不支持任何控件模式；例如，不能移动、调整大小或停靠的窗格没有任何控件模式。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 支持由标识的自定义控件<xref:System.Windows.Automation.ControlType.Custom>属性和可通过描述<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>属性。  
  
 下表显示了 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 角色到 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控件类型的映射。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Role — 角色|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控件类型|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Button|  
|ROLE_SYSTEM_CLIENT|Calendar|  
|ROLE_SYSTEM_CHECKBUTTON|复选框|  
|ROLE_SYSTEM_COMBOBOX|组合框|  
|ROLE_SYSTEM_CLIENT|自定义|  
|ROLE_SYSTEM_LIST|数据网格|  
|ROLE_SYSTEM_LISTITEM|数据项|  
|ROLE_SYSTEM_DOCUMENT|Document|  
|ROLE_SYSTEM_TEXT|Edit|  
|ROLE_SYSTEM_GROUPING|Group|  
|ROLE_SYSTEM_LIST|Header|  
|ROLE_SYSTEM_COLUMNHEADER|标头项|  
|ROLE_SYSTEM_LINK|超链接|  
|ROLE_SYSTEM_GRAPHIC|图像|  
|ROLE_SYSTEM_LIST|列表|  
|ROLE_SYSTEM_LISTITEM|列表项|  
|ROLE_SYSTEM_MENUPOPUP|菜单|  
|ROLE_SYSTEM_MENUBAR|菜单栏|  
|ROLE_SYSTEM_MENUITEM|Menu item|  
|ROLE_SYSTEM_PANE|Pane|  
|ROLE_SYSTEM_PROGRESSBAR|进度栏|  
|ROLE_SYSTEM_RADIOBUTTON|单选按钮|  
|ROLE_SYSTEM_SCROLLBAR|滚动条|  
|ROLE_SYSTEM_SEPARATOR|Separator|  
|ROLE_SYSTEM_SLIDER|Slider|  
|ROLE_SYSTEM_SPINBUTTON|Spinner|  
|ROLE_SYSTEM_SPLITBUTTON|“拆分”按钮|  
|ROLE_SYSTEM_STATUSBAR|状态栏|  
|ROLE_SYSTEM_PAGETABLIST|Tab|  
|ROLE_SYSTEM_PAGETAB|选项卡项|  
|ROLE_SYSTEM_TABLE|表|  
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|Thumb|  
|ROLE_SYSTEM_TITLEBAR|标题栏|  
|ROLE_SYSTEM_TOOLBAR|工具栏|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|树|  
|ROLE_SYSTEM_OUTLINEITEM|树项|  
|ROLE_SYSTEM_WINDOW|窗口|  
  
 有关不同控件类型的更多信息，请参阅 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)。  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>状态和属性  
 在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中，元素支持一组通用的属性集，且某些属性（如 `accState`）必须描述截然不同的事物，具体取决于元素的角色。 服务器必须实现可返回属性的 `IAccessible` 的所有方法，返回的属性甚至与该元素不相关。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 定义多个属性，其中一些对应于状态中[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]。 某些属性是所有元素共有的，但其他属性特定于控件类型和控件模式。 属性由唯一标识符进行区分，并且大多数属性都可通过使用单个方法 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> 或 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>进行检索。 许多属性还可以轻松从 <xref:System.Windows.Automation.AutomationElement.Current%2A> 和 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 属性访问器进行检索。  
  
 UI 自动化提供程序不需要实现不相关的属性，而可以只返回任何其不支持的属性的 `null`值。 此外， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服务可以从默认窗口提供程序获取一些属性，并且这些属性与提供程序显式实现的属性相合并。  
  
 除了支持更多属性外， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 通过允许使用单一跨进程调用检索多个属性来提供更好的性能。  
  
 下表显示了两个模型中属性之间的对应关系。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 属性访问器|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性 ID|备注|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> 或 <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` 如果两者都存在，请将优先。|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|请参阅上表，了解角色到控件类型的映射。|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|仅对支持 ValuePattern 或 RangeValuePattern 的控件类型有效。 RangeValue 值被规范化为 0-100，与 MSAA 行为保持一致。 值项使用一个字符串。|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|中不支持 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` 没有清晰的规范，从而产生了提供程序信息的不同部分置于此属性在 MSAA 内。|  
|`get_accHelpTopic`|中不支持 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 下表显示了哪些 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性对应于 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 状态常量。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] state|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性|是否触发状态更改？|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|对于复选框， <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> 对于单选按钮， <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> 或 <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> 为菜单项|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True 和<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>导致 <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> 支持|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 以下状态或者未由大多数 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 控制服务器实现，或者在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中没有等效项。  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] state|备注|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]服务器广泛实现|  
|STATE_SYSTEM_MARQUEED|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_SELFVOICING|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_TRAVERSED|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_ALERT_MEDIUM|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_ALERT_LOW|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_FLOATING|未通过 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 服务器广泛实现|  
|STATE_SYSTEM_HOTTRACKED|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|在中不可用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性标识符的完整列表，请参阅 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)。  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>事件  
 不同于 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中的事件机制， [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中的事件机制不依赖于 Windows 事件路由（使用窗口句柄紧密连接）且不需要客户端应用程序来设置挂钩。 可以对事件订阅进行微调，不仅能订阅特定事件，甚至还能订阅树的特定部分。 通过跟踪所侦听的事件，提供程序也可微调其事件的引发。  
  
 对于客户端来说检索引发事件的元素也很简单，因为这些事件会被直接传递到事件回调。 如果在客户端订阅该事件时，缓存请求处于活动状态，则会自动预提取元素的属性。  
  
 下表显示了 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvent 和 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件的对应关系。  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件标识符|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> 属性更改|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>相关联的滚动条上的属性更改|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|无等效项|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|没有确切的等效项；也许 <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 或 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> 属性更改|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> 更改|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 属性更改|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> 属性更改|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|在 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]中使用不一致。 在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]中没有定义直接对应的事件。|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|无等效项|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|各种属性更改事件|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> 和<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType>更改|  
|EVENT_SYSTEM_ALERT|无等效项|  
|EVENT_SYSTEM_CAPTUREEND|无等效项|  
|EVENT_SYSTEM_CAPTURESTART|无等效项|  
|EVENT_SYSTEM_CONTEXTHELPEND|无等效项|  
|EVENT_SYSTEM_CONTEXTHELPSTART|无等效项|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|无等效项|  
|EVENT_SYSTEM_DRAGDROPSTART|无等效项|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 属性更改|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 属性更改|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 属性更改|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> 属性更改|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>属性更改|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 或<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>属性更改|  
|EVENT_SYSTEM_SOUND|无等效项|  
|EVENT_SYSTEM_SWITCHEND|没有等效项，但 <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> 事件表示新的应用程序已收到焦点|  
|EVENT_SYSTEM_SWITCHSTART|无等效项|  
|无等效项|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> 属性更改|  
|无等效项|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> Event — 事件|  
|无等效项|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>安全性  
 某些 `IAccessible` 自定义应用场景需要包装一个基本 `IAccessible` 并对其调用。 这具有安全隐患，因为部分受信任的组件不应为代码路径上的中介。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 模型使提供程序不再需要通过其他提供程序代码调用。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心服务将进行所有必要的聚合。  
  
## <a name="see-also"></a>请参阅

- [UI 自动化基础知识](../../../docs/framework/ui-automation/index.md)
