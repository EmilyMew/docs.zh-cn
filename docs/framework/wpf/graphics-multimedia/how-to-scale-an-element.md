---
title: 如何：缩放元素
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131698"
---
# <a name="how-to-scale-an-element"></a>如何：缩放元素
此示例演示如何使用<xref:System.Windows.Media.ScaleTransform>缩放元素。  
  
 使用<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>属性以调整元素大小由指定的系数。 例如，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>值为 1.5 会拉伸到其原始宽度的 150%的元素。 一个<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>值为 0.5 会元素的高度缩小 50%。  
  
 使用<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>属性来指定缩放操作的中心点。 默认情况下，<xref:System.Windows.Media.ScaleTransform>对应于矩形的左上角的点 (0，0) 的中心。 此操作将移动元素的以及使其看上去更大，因为当应用<xref:System.Windows.Media.Transform>，更改该对象所驻留的坐标空间。  
  
 下面的示例使用<xref:System.Windows.Media.ScaleTransform>翻倍，大小为 50 的 50 <xref:System.Windows.Shapes.Rectangle>。 <xref:System.Windows.Media.ScaleTransform>两个具有值为 0 （默认值）<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>。  
  
## <a name="example"></a>示例  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常情况下，设置<xref:System.Windows.Media.ScaleTransform.CenterX%2A>并<xref:System.Windows.Media.ScaleTransform.CenterY%2A>到中心进行缩放的对象: (<xref:System.Windows.FrameworkElement.Width%2A>/2，  <xref:System.Windows.FrameworkElement.Height%2A> /2)。  
  
 下面的示例演示了另一个<xref:System.Windows.Shapes.Rectangle>的一倍大小; 但是，这<xref:System.Windows.Media.ScaleTransform>两个具有值为 25<xref:System.Windows.Media.ScaleTransform.CenterX%2A>和<xref:System.Windows.Media.ScaleTransform.CenterY%2A>，这对应于矩形的中心。  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 下图显示了两者之间的差异<xref:System.Windows.Media.ScaleTransform>操作。 虚线显示的是矩形在缩放之前的大小和位置。  
  
 ![以不同中心点的 2 倍缩放](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
两个具有相同 ScaleX 和 ScaleY 值但中心不同的 ScaleTransform 操作  
  
 有关完整示例，请参阅 [2D 转换示例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [变换概述](transforms-overview.md)
- [帮助主题](transformations-how-to-topics.md)
