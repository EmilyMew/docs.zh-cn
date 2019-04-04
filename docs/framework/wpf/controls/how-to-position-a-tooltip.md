---
title: 如何：定位 ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 64b3823be5203ffcb9dcea371495dbb6ead1605f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840492"
---
# <a name="how-to-position-a-tooltip"></a>如何：定位 ToolTip
此示例演示如何在屏幕上指定的工具提示的位置。  
  
## <a name="example"></a>示例  
 可以使用一组中都定义的五个属性来定位 tooltip<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>类。 下表显示了这两个五个属性集，并提供指向其根据类的参考文档。  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>类根据相应的工具提示属性  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> 类属性|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> 类属性|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 如果您通过使用定义的工具提示内容<xref:System.Windows.Controls.ToolTip>对象，可以使用其中一个类的属性; 但是，<xref:System.Windows.Controls.ToolTipService>属性优先。 使用<xref:System.Windows.Controls.ToolTipService>属性未定义为的工具提示<xref:System.Windows.Controls.ToolTip>对象。  
  
 下图显示如何使用这些属性来定位 tooltip。 虽然，则[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]在这些说明中的示例演示如何设置所定义的属性<xref:System.Windows.Controls.ToolTip>类的相应属性<xref:System.Windows.Controls.ToolTipService>类遵循相同的布局规则。 有关位置属性的可能值的详细信息，请参阅[Popup 放置行为](popup-placement-behavior.md)。  
 
 下图显示工具提示放置了通过使用放置属性：  
  
 ![通过使用放置属性显示工具提示放置关系图。](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 下图显示工具提示放置了通过使用放置和 PlacementRectangle 属性：   

 ![通过使用 PlacementRectangle 属性显示工具提示放置关系图。](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 下图显示工具提示放置了通过使用放置、 PlacementRectangle 和偏移量属性：   
  
 ![通过使用偏移量属性显示工具提示放置关系图。](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 下面的示例演示如何使用<xref:System.Windows.Controls.ToolTip>属性来指定其内容的工具提示的位置<xref:System.Windows.Controls.ToolTip>对象。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 下面的示例演示如何使用<xref:System.Windows.Controls.ToolTipService>属性来指定其内容不是一个工具提示的位置<xref:System.Windows.Controls.ToolTip>对象。  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [帮助主题](tooltip-how-to-topics.md)
- [ToolTip 概述](tooltip-overview.md)
