---
title: ProgressBar 样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: f948cf2b4f4cd2a4cb73b0cd5fc754240c850b83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099412"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar 样式和模板
本主题介绍的样式和模板的<xref:System.Windows.Controls.ProgressBar>控件。 可以修改默认<xref:System.Windows.Controls.ControlTemplate>为控件提供唯一外观。 有关详细信息，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="progressbar-parts"></a>ProgressBar 部件  
 下表列出了用于命名的部件<xref:System.Windows.Controls.ProgressBar>控件。  
  
|部件|类型|描述|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|一个对象，它指示进度。|  
|PART_Track|<xref:System.Windows.FrameworkElement>|定义进度指示器的路径的对象。|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|一个对象，修饰进度栏。|  
  
## <a name="progressbar-states"></a>进度栏状态  
 下表列出了的可视状态<xref:System.Windows.Controls.ProgressBar>控件。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|----------------------|---------------------------|-----------------|  
|确定|CommonStates|<xref:System.Windows.Controls.ProgressBar> 报告进度基于<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>属性。|  
|不确定|CommonStates|<xref:System.Windows.Controls.ProgressBar> 报告由重复图案泛型进度。|  
|有效|ValidationStates|该控件使用<xref:System.Windows.Controls.Validation>类和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`已在控件有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性是`true`具有该控件没有焦点。|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate 示例  
 下面的示例演示如何定义<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.ProgressBar>控件。  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 上一示例使用了一个或多个以下资源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Control 样式和模板](control-styles-and-templates.md)
- [控件自定义](control-customization.md)
- [样式设置和模板化](styling-and-templating.md)
- [通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)
