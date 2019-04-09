---
title: 如何：修改直线或线段末端的线帽
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 462e32520393a1c23809cce8eb3c130c13bc882f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091299"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>如何：修改直线或线段末端的线帽
此示例演示如何修改处的开始或结束的一种开放的形状<xref:System.Windows.Shapes.Shape>元素。 若要更改在打开的开始处上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>属性。 若要更改末尾的一种开放上限<xref:System.Windows.Shapes.Shape>，使用其<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>属性。 若要查看可用的线帽，请参阅<xref:System.Windows.Media.PenLineCap>枚举。  
  
> [!NOTE]
>  此属性才影响开放式形状，如<xref:System.Windows.Shapes.Line>、 一个<xref:System.Windows.Shapes.Polyline>，或打开<xref:System.Windows.Shapes.Path>元素。  
  
 下面的示例绘制了四个<xref:System.Windows.Shapes.Polyline>元素，并在每个端点上使用一组不同的形状。  
  
## <a name="example"></a>示例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 此示例摘自一个更大的示例;有关完整示例，请参阅[形状元素示例](https://go.microsoft.com/fwlink/?LinkID=160037)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
