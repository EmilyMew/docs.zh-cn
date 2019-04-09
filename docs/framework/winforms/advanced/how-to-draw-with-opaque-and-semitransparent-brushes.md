---
title: 如何：用不透明和半透明的画笔绘制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100909"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>如何：用不透明和半透明的画笔绘制
当填充形状时，必须将 <xref:System.Drawing.Brush> 对象传递到 <xref:System.Drawing.Graphics> 类的填充方法之一。 <xref:System.Drawing.SolidBrush.%23ctor%2A> 构造函数的参数是 <xref:System.Drawing.Color> 对象。 若要填充不透明的形状，将颜色的 alpha 分量设置为 255。 若要填充半透明的形状，将 alpha 分量设置为从 1 到 254 之间的任何值。  
  
 当填充半透明形状时，形状的颜色与背景的颜色混合。 alpha 分量指定形状颜色和背景色混合的方式；alpha 值越接近 0，背景颜色的比重越大，alpha 值越接近 255，形状颜色的比重越大。  
  
## <a name="example"></a>示例  
 以下示例绘制位图，然后填充重叠位图的三个椭圆。 第一个椭圆使用值为 255 的 alpha 分量，因此它是不透明的。 第二个和第三个椭圆使用值为 128 的 alpha 分量，因此它们是半透明的；还可透过椭圆看到背景图像。 设置 <xref:System.Drawing.Graphics.CompositingQuality%2A> 属性的调用会导致第三个椭圆的混合与灰度校正联合完成。  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 下图显示了以下代码的输出： 
  
 ![显示不透明和半透明的输出的图例。](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [Alpha 混合线条和填充](alpha-blending-lines-and-fills.md)
- [如何：使控件拥有透明背景](../controls/how-to-give-your-control-a-transparent-background.md)
- [如何：绘制不透明和半透明的线条](how-to-draw-opaque-and-semitransparent-lines.md)
