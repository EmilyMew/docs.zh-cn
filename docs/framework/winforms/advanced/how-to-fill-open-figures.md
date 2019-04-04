---
title: 如何：填充开放图形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: c7d193fdad554048ecd0f2cca5a83cfccbc2a403
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654076"
---
# <a name="how-to-fill-open-figures"></a>如何：填充开放图形
可以通过传递填充路径<xref:System.Drawing.Drawing2D.GraphicsPath>对象传递给<xref:System.Drawing.Graphics.FillPath%2A>方法。 <xref:System.Drawing.Graphics.FillPath%2A>方法填充填充模式 （备用或缠绕） 根据当前设置的路径的路径。 如果该路径包含任何开放的图形，就像这些图形闭合填充的路径。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 通过从其结束点到起始点绘制一条直线，闭合图。  
  
## <a name="example"></a>示例  
 以下示例创建具有一个开放的图形 (arc) 和一个闭合的图形 （椭圆） 的路径。 <xref:System.Drawing.Graphics.FillPath%2A>方法填充默认值填充模式中，是根据路径<xref:System.Drawing.Drawing2D.FillMode.Alternate>。  
  
 下图显示了示例代码的输出。 请注意，填充路径 (根据<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 像打开图关闭的一条直线从其结束点到起始点。  
  
 ![图示显示 FillPath 方法的输出](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [GDI+ 中的图形路径](graphics-paths-in-gdi.md)
