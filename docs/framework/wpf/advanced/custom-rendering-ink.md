---
title: 自定义呈现墨迹
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: fead6e28949726bef46fe2be46e976fb47c3e9a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125653"
---
# <a name="custom-rendering-ink"></a>自定义呈现墨迹
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>笔划的属性，可指定笔划，其大小、 颜色和形状，如的外观，但可能有些时候你想要自定义外观更<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>允许。 建议通过使用喷笔、油画和多种其他效果呈现外观，从而自定义墨迹的外观。 Windows Presentation Foundation (WPF) 允许您为自定义通过实现自定义呈现墨迹<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>和<xref:System.Windows.Ink.Stroke>对象。  
  
 本主题包含以下小节：  
  
-   [体系结构](#Architecture)  
  
-   [实现动态呈现器](#ImplementingADynamicRenderer)  
  
-   [实现自定义笔划](#ImplementingCustomStrokes)  
  
-   [实现自定义 InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [结束语](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>体系结构  
 墨迹呈现会出现两次：用户将墨迹写入墨迹书写表面时，以及将笔划添加到启用了墨迹的表面之后。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>当用户移动触笔数字化仪上, 呈现墨迹和<xref:System.Windows.Ink.Stroke>添加到元素后呈现自身。  
  
 动态呈现墨迹时需要实现三个类。  
  
1.  **DynamicRenderer**:实现从 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 派生的类。 此类是一个专用<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的形式对其绘制呈现笔划。 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>上执行呈现一个单独的线程，因此墨迹书写表面显示为收集手写内容，即使应用程序用户界面 (UI) 线程被阻止。 有关线程模型的详细信息，请参阅[墨迹线程模型](the-ink-threading-model.md)。 若要自定义动态呈现笔划，请重写<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。  
  
2.  **笔划**:实现从 <xref:System.Windows.Ink.Stroke> 派生的类。 此类负责的静态呈现<xref:System.Windows.Input.StylusPoint>数据转换为后<xref:System.Windows.Ink.Stroke>对象。 重写<xref:System.Windows.Ink.Stroke.DrawCore%2A>方法，以确保静态呈现笔划的是与动态呈现一致。  
  
3.  **在 InkCanvas:** 实现从 <xref:System.Windows.Controls.InkCanvas> 派生的类。 分配的自定义<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>到<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>属性。 重写<xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>方法并添加到自定义笔划<xref:System.Windows.Controls.InkCanvas.Strokes%2A>属性。 这样可以确保墨迹外观一致。  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>实现动态呈现器  
 尽管<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>类是标准的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，若要执行更专业的呈现，则必须创建派生的自定义动态呈现器<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>并重写<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>方法。  
  
 下面的示例演示自定义<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>绘制带有线性渐变画笔效果的墨迹。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>实现自定义笔划  
 实现从 <xref:System.Windows.Ink.Stroke> 派生的类。 此类负责呈现<xref:System.Windows.Input.StylusPoint>数据转换为后<xref:System.Windows.Ink.Stroke>对象。 重写<xref:System.Windows.Ink.Stroke.DrawCore%2A>类来进行实际绘制。  
  
 笔划类还可以通过使用存储自定义数据<xref:System.Windows.Ink.Stroke.AddPropertyData%2A>方法。 此数据持续存在时会与笔划数据一起存储。  
  
 <xref:System.Windows.Ink.Stroke>类还可以执行命中测试。 您还可以实现你自己的命中测试算法通过重写<xref:System.Windows.Ink.Stroke.HitTest%2A>中当前类的方法。  
  
 以下C#的代码演示了一个自定义<xref:System.Windows.Ink.Stroke>呈现类的<xref:System.Windows.Input.StylusPoint>为三维笔划的数据。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>实现自定义 InkCanvas  
 使用你的自定义的最简单办法<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>笔划是实现派生自的类和<xref:System.Windows.Controls.InkCanvas>并使用这些类。 <xref:System.Windows.Controls.InkCanvas>具有<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>指定当用户绘制笔划的呈现方式的属性。  
  
 自定义上呈现笔画<xref:System.Windows.Controls.InkCanvas>执行以下操作：  
  
-   创建派生一个类<xref:System.Windows.Controls.InkCanvas>。  
  
-   分配你的自定义<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>到<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType>属性。  
  
-   重写 <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> 方法。 使用此方法时，请删除之前添加到 InkCanvas 的原始笔划。 然后创建一个自定义笔划，将其添加到<xref:System.Windows.Controls.InkCanvas.Strokes%2A>属性，并调用具有一个新的基本类<xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs>，其中包含自定义笔划。  
  
 以下C#的代码演示了一个自定义<xref:System.Windows.Controls.InkCanvas>类，该类使用自定义<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>，并收集自定义笔划。  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas>可以有多个<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。 可以添加多个<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>对象添加到<xref:System.Windows.Controls.InkCanvas>通过将它们添加到<xref:System.Windows.UIElement.StylusPlugIns%2A>属性。  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>结束语  
 您可以通过派生您自己自定义墨迹的外观<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>， <xref:System.Windows.Ink.Stroke>，和<xref:System.Windows.Controls.InkCanvas>类。 将这些类结合使用可以确保用户绘制笔划时和笔划被收集后的笔划外观保持一致。  
  
## <a name="see-also"></a>请参阅

- [高级墨迹处理](advanced-ink-handling.md)
