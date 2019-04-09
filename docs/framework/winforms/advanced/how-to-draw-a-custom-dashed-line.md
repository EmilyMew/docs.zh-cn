---
title: 如何：绘制自定义虚线
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109182"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>如何：绘制自定义虚线
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了多个短划线样式中列出的<xref:System.Drawing.Drawing2D.DashStyle>枚举。 如果这些标准的短划线样式无法满足您的需要，可以创建自定义的短划线图案。  
  
## <a name="example"></a>示例  
 若要绘制自定义虚线，放置在数组中的短划线和空格的长度，并将数组分配的值为<xref:System.Drawing.Pen.DashPattern%2A>属性的<xref:System.Drawing.Pen>对象。 下面的示例绘制自定义虚线基于数组上`{5, 2, 15, 4}`。 如果您要乘以钢笔的宽度为 5 数组的元素，则获取`{25, 10, 75, 20}`。 显示的短划线的长度介于 25 和 75，之间交替，空格交替出现在 10 和 20 之间的长度。  
  
 下图显示了生成的虚线。 请注意，最终的短划线必须是少于 25 个单位，以便在线条的终点 （405，5）。  
  
 ![显示一条虚线的图例。](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>编译代码  
 创建 Windows 窗体和处理该窗体<xref:System.Windows.Forms.Control.Paint>事件。 前面将代码粘贴到<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅

- [使用钢笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
