---
title: Menu 样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 6818be4ac92dbdd7de0c6c6fa65109e21eadc2f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094198"
---
# <a name="menu-styles-and-templates"></a>Menu 样式和模板
本主题介绍的样式和模板的<xref:System.Windows.Controls.Menu>控件。 可以修改默认<xref:System.Windows.Controls.ControlTemplate>为控件提供唯一外观。 有关详细信息，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="menu-parts"></a>菜单部分  
 <xref:System.Windows.Controls.Menu>控件没有任何命名的部件。  
  
 当您创建<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.Menu>，模板可能包含<xref:System.Windows.Controls.ItemsPresenter>内<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>显示在每个项<xref:System.Windows.Controls.Menu>;<xref:System.Windows.Controls.ScrollViewer>控件内实现滚动)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子级<xref:System.Windows.Controls.ScrollViewer>，必须授予<xref:System.Windows.Controls.ItemsPresenter>名称， `ItemsPresenter`。  
  
## <a name="menu-states"></a>菜单状态  
 下表列出了的可视状态<xref:System.Windows.Controls.Menu>控件。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|有效|ValidationStates|该控件使用<xref:System.Windows.Controls.Validation>类和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`已在控件有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`具有该控件没有焦点。|  
  
## <a name="menuitem-parts"></a>菜单项部分  
 下表列出了用于命名的部件<xref:System.Windows.Controls.Menu>控件。  
  
|部件|类型|描述|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|用于子菜单的区域。|  
  
 当您创建<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.MenuItem>，模板可能包含<xref:System.Windows.Controls.ItemsPresenter>内<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>显示在每个项<xref:System.Windows.Controls.MenuItem>;<xref:System.Windows.Controls.ScrollViewer>控件内实现滚动)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子级<xref:System.Windows.Controls.ScrollViewer>，必须授予<xref:System.Windows.Controls.ItemsPresenter>名称， `ItemsPresenter`。  
  
## <a name="menuitem-states"></a>菜单项状态  
 下表列出了的可视状态<xref:System.Windows.Controls.MenuItem>控件。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|有效|ValidationStates|该控件使用<xref:System.Windows.Controls.Validation>类和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`已在控件有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`具有该控件没有焦点。|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>菜单和菜单项 ControlTemplate 示例  
 下面的示例演示如何定义<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Menu>控件。  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 下面的示例演示如何定义<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.MenuItem>控件。  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 下面的示例定义`MenuScrollViewer`，会在上一示例中使用。  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <xref:System.Windows.Controls.ControlTemplate>示例使用一个或多个以下资源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Control 样式和模板](control-styles-and-templates.md)
- [控件自定义](control-customization.md)
- [样式设置和模板化](styling-and-templating.md)
- [通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)
