---
title: 实现 UI 自动化 Selection 控件模式
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: b5ca41c5dafe42a9afbd8390713f099c167d2020
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673309"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>实现 UI 自动化 Selection 控件模式
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主题介绍了实现 <xref:System.Windows.Automation.Provider.ISelectionProvider>的准则和约定，包括有关事件和属性的信息。 本主题的结尾列出了指向其他参考资料的链接。  
  
 <xref:System.Windows.Automation.SelectionPattern> 控件模式用于支持作为可选子项集合的容器的控件。 此元素的子级必须实现 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。 有关实现此控件模式的控件示例，请参阅 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>实现准则和约定  
 在实现“选项”控件模式时，请注意以下准则和约定：  
  
-   实现 <xref:System.Windows.Automation.Provider.ISelectionProvider> 的控件允许选择单个或多个子项。 例如，列表框、列表视图和树视图支持多个选项，而组合框、滑块和单选按钮组则支持单个选项。  
  
-   具有最小、最大和连续范围的控件（如“卷”  滑块控件）应实现 <xref:System.Windows.Automation.Provider.IRangeValueProvider> 而不是 <xref:System.Windows.Automation.Provider.ISelectionProvider>。  
  
-   管理实现 <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>的子控件的单选控件（如“显示属性”  对话框中的“屏幕分辨率”  滑块，或 **中的“颜色选取器”**[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] 选项控件（如下所示））应实现 <xref:System.Windows.Automation.Provider.ISelectionProvider>；其子级应实现 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> 和 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。  
  
 ![突出显示黄色的颜色选取器。](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
颜色样本字符串映射的示例  
  
-   菜单不支持 <xref:System.Windows.Automation.SelectionPattern>。 如果你正在处理包含图形和文本的菜单项（例如， **中的“视图”** **菜单中的“预览窗格”** [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]项）并需要传达状态，则应实现 <xref:System.Windows.Automation.Provider.IToggleProvider>。  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>ISelectionProvider 必需的成员  
 以下属性、方法和事件都是 <xref:System.Windows.Automation.Provider.ISelectionProvider> 接口所必需的。  
  
|必需的成员|类型|说明|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|属性|应支持使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>的属性更改事件。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|属性|应支持使用 <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> 和 <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>的属性更改事件。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|方法|None|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Event|在容器中的选项发生重大更改并需要发送多于 <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> 常量所允许的添加和移除事件时引发。|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 和 <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> 属性可以是动态的。 例如，控件的初始状态默认可能未选择任何项，指示 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> 是 `false`。 但是，选择某一项后，该控件必须始终具有至少一个选定的项。 同样，在极少数情况下，控件可能允许在初始状态下选择多个项，但随后仅允许选择一个选项。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceptions  
 提供程序必须引发以下异常。  
  
|异常类型|条件|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|如果未启用该控件。|  
|<xref:System.InvalidOperationException>|如果该控件是隐藏的。|  
  
## <a name="see-also"></a>请参阅
- [UI 自动化控件模式概述](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [在 UI 自动化提供程序中支持控件模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [客户端的 UI 自动化控件模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [实现 UI 自动化 SelectionItem 控件模式](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [UI 自动化树概述](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [在 UI 自动化中使用缓存](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
