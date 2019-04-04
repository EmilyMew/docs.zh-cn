---
title: 使用自动布局概述
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 74c4e10e8f28fb00a5528c1ab860b88d0caa4303
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408751"
---
# <a name="use-automatic-layout-overview"></a>使用自动布局概述
本主题介绍如何编写上面向开发人员的指导原则[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]具有可本地化的应用程序[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]。 在过去，UI 的本地化是一个耗时的过程。 UI 适用于每种语言需要按像素逐一调整。 使用适当的设计和编码标准，今天[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]可以构建，这样本地化人员较少的调整大小和重新定位的工作量。 种编写可以更轻松地重设大小和重新定位应用程序的方法称为自动布局，可以通过使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序设计。  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>使用自动布局的优点  
 因为[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的演示系统，是功能强大且灵活，它提供到可以进行调整以适应不同语言的要求的应用程序中的布局元素的功能。 下面列出自动布局的部分优点。  

-   UI 会显示在任何语言中。  

-   减少了文本转换完后重新调整控件位置和大小的需要。  
  
-   减少了重新调整窗口大小的需要。  

-   UI 布局中的任何语言正确呈现。  

-   本地化过程可缩减为与进行字符串转换差不多。  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>自动布局和控件  
 利用自动布局，应用程序可以自动调整控件大小。 例如，控件可按字符串长度相应改变。 利用此功能，本地化人员可转换字符串，而无需再调整控件大小以适应转换后的文本。 下面的示例创建一个带有英文内容的按钮。  
  
 [!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 在此示例中，只需更改文本即可生成一个西班牙文按钮。 例如，应用于对象的  
  
 [!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下图显示了代码示例的输出：  
  
 ![具有不同语言的文本的同一按钮](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>自动布局和编码标准  
 使用自动布局方法需要一组编码和设计标准和规则以生成可完全本地化的 UI。 下列准则可帮助完成自动布局编码。  

**不要使用绝对位置**

- 不要使用<xref:System.Windows.Controls.Canvas>因为它会以绝对方式定位元素。

- 使用<xref:System.Windows.Controls.DockPanel>， <xref:System.Windows.Controls.StackPanel>，和<xref:System.Windows.Controls.Grid>来定位控件。

有关各种面板类型的讨论，请参阅[面板概述](../controls/panels-overview.md)。

**未设置固定的大小的窗口**

- 请使用 <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>。 例如：

   [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**添加 <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- 添加<xref:System.Windows.FrameworkElement.FlowDirection%2A>到你的应用程序的根元素。

   WPF 提供了方便地支持水平、 双向和垂直布局。 在演示框架<xref:System.Windows.FrameworkElement.FlowDirection%2A>属性可以用于定义布局。 流方向模式包括：
   
     - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — 拉丁语、 东亚语言等的水平布局。
     
     - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — 有关阿拉伯语、 希伯来语等双向。

**使用复合字体而不是物理字体**

- 使用复合字体<xref:System.Windows.Controls.Control.FontFamily%2A>属性不需要进行本地化。

- 开发人员可以使用以下字体之一，也可以创建自己的字体。

   - Global User Interface
   - Global San Serif
   - Global Serif

**添加 xml: lang**

- 添加`xml:lang`特性中的根元素的 UI，如`xml:lang="en-US"`英文应用程序。

- 因为复合字体使用`xml:lang`若要确定要使用的字体，请设置此属性以支持多语言方案。

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>自动布局和网格  
 <xref:System.Windows.Controls.Grid>元素，是对于自动布局很有用，因为它使开发人员来定位元素。 一个<xref:System.Windows.Controls.Grid>控件是支持的分发在其子元素，使用列和行排列方式的可用空间。 UI 元素可以跨多个单元格，并且可能具有在网格内的网格。 网格非常有用，因为它们使您能够创建和定位复杂的 UI。 下面的示例演示使用网格来定位某些按钮和文本。 请注意，高度和宽度的单元格设置为<xref:System.Windows.GridUnitType.Auto>; 因此，包含带图像按钮的单元格调整以适合图像。  

 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下图显示了以上代码生成的网格。  
  
 ![网格示例](./media/glob-grid.png "glob_grid")  
Grid  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>使用 IsSharedSizeScope 属性的自动布局和网格  
 一个<xref:System.Windows.Controls.Grid>元素是可本地化的应用程序创建进行调整以适应内容的控件中很有用。 不过，有时可能希望控件无论包含什么内容都可以保持特定大小。 例如，对于“确定”、“取消”和“浏览”按钮，可能不希望按钮根据内容调整大小。 在这种情况下<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType>附加的属性可用于共享多个网格元素之间同样的大小。 下面的示例演示如何共享列和行的大小之间多个数据<xref:System.Windows.Controls.Grid>元素。  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **请注意**完整的代码示例，请参阅[共享大小调整属性网格之间](../controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>请参阅
- [WPF 全球化](globalization-for-wpf.md)
- [使用自动布局创建按钮](how-to-use-automatic-layout-to-create-a-button.md)
- [使用网格进行自动布局](how-to-use-a-grid-for-automatic-layout.md)
