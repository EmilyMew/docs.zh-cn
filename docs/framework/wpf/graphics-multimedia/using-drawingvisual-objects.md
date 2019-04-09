---
title: 使用 DrawingVisual 对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 01e10a4b0f0bf4959850caf3951ad4ea915edb4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121714"
---
# <a name="using-drawingvisual-objects"></a>使用 DrawingVisual 对象
本主题概述了如何使用<xref:System.Windows.Media.DrawingVisual>中的对象[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可视化层。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual 对象  
 <xref:System.Windows.Media.DrawingVisual>是一个轻量绘图类，用于呈现形状、 图像或文本。 此类之所以为轻量类是因为它不提供布局或事件处理，从而性能得以提升。 因此，绘图非常适用于背景和剪贴画。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual 宿主容器  
 若要使用<xref:System.Windows.Media.DrawingVisual>对象，您需要创建宿主容器对象。 宿主容器对象必须派生自<xref:System.Windows.FrameworkElement>类，该类提供的布局和事件处理支持<xref:System.Windows.Media.DrawingVisual>类缺少。 宿主容器对象不显示任何可视属性，因为它的主要用途是包含子对象。 但是，<xref:System.Windows.UIElement.Visibility%2A>宿主容器的属性必须设置为<xref:System.Windows.Visibility.Visible>; 否则为 none 及其子元素将可见。  
  
 在创建视觉对象宿主容器对象时，您必须将存储中的视觉对象引用<xref:System.Windows.Media.VisualCollection>。 使用<xref:System.Windows.Media.VisualCollection.Add%2A>方法将视觉对象添加到宿主容器。 以下示例中，在创建宿主容器对象，并且三个视觉对象添加到其<xref:System.Windows.Media.VisualCollection>。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  有关从中提取上述代码示例的完整代码示例，请参阅[使用 DrawingVisual 的命中测试示例](https://go.microsoft.com/fwlink/?LinkID=159994)。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>创建 DrawingVisual 对象  
 当你创建<xref:System.Windows.Media.DrawingVisual>对象，它不包含任何绘图内容。 可以通过检索对象的添加文本、 图形或图像内容<xref:System.Windows.Media.DrawingContext>和在其中进行绘制。 一个<xref:System.Windows.Media.DrawingContext>返回通过调用<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>方法的<xref:System.Windows.Media.DrawingVisual>对象。  
  
 若要绘制到一个矩形<xref:System.Windows.Media.DrawingContext>，使用<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>方法的<xref:System.Windows.Media.DrawingContext>对象。 对于绘制其他类型的内容，存在类似的方法。 完成内容绘制到时<xref:System.Windows.Media.DrawingContext>，调用<xref:System.Windows.Media.DrawingContext.Close%2A>方法关闭<xref:System.Windows.Media.DrawingContext>并保存内容。  
  
 在以下示例中，<xref:System.Windows.Media.DrawingVisual>创建对象，和一个矩形绘制到其<xref:System.Windows.Media.DrawingContext>。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>为 FrameworkElement 成员创建重写  
 宿主容器对象负责管理其视觉对象的集合。 这要求宿主容器实现为派生的成员重写<xref:System.Windows.FrameworkElement>类。  
  
 下表介绍了必须重写的两个成员：  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>:返回子元素的集合中的指定索引处的子级。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>:获取此元素内可视子元素的数目。  
  
 在以下示例中，重写为两个<xref:System.Windows.FrameworkElement>成员实现。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>提供命中测试支持  
 宿主容器对象可以提供事件处理，即使它不显示任何可视属性，但是，其<xref:System.Windows.UIElement.Visibility%2A>属性必须设置为<xref:System.Windows.Visibility.Visible>。 这样便可以为宿主容器创建事件处理例程，此例程可以捕获鼠标事件，如松开鼠标左键。 然后，事件处理例程可以实现命中测试通过调用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。 该方法的<xref:System.Windows.Media.HitTestResultCallback>参数是指可用于确定生成的命中测试操作的用户定义的过程。  
  
 在下面的示例中，为宿主容器对象及其子级实现命中测试支持。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF 图形呈现疑难解答](wpf-graphics-rendering-overview.md)
- [可视化层中的命中测试](hit-testing-in-the-visual-layer.md)
