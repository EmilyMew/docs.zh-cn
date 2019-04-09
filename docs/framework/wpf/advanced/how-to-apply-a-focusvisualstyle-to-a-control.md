---
title: 如何：向控件应用 FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133544"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>如何：向控件应用 FocusVisualStyle
此示例演示如何在资源中创建焦点视觉样式并将样式应用到控件时，使用<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>属性。  
  
## <a name="example"></a>示例  
 下面的示例定义的样式，将创建仅在该控件是中的键盘焦点时应用的其他控件组合[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 这通过定义样式与实现<xref:System.Windows.Controls.ControlTemplate>，然后在设置时，为资源引用该样式<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>属性。  
  
 类似于边框外部矩形放置之外的矩形区域。 除非修改，否则使用的样式的大小调整<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>焦点视觉样式应用的位置的矩形控件。 此示例设置值为负值<xref:System.Windows.FrameworkElement.Margin%2A>以使显示稍有外部具有焦点的控件的边框。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 一个<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>是附加到提供任何控件模板样式从显式样式或主题样式; 主样式的控件仍可创建使用<xref:System.Windows.Controls.ControlTemplate>并将该样式设置为<xref:System.Windows.FrameworkElement.Style%2A>属性。  
  
 焦点视觉样式应始终在主题或 UI，而不是使用另一个用于每个可获得焦点的元素。 有关详细信息，请参阅[的控件和 FocusVisualStyle 焦点设置样式](styling-for-focus-in-controls-and-focusvisualstyle.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [样式设置和模板化](../controls/styling-and-templating.md)
- [为控件中的焦点设置样式以及 FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
