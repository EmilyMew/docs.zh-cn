---
title: 如何：在 Windows 窗体中复制像素以减少闪烁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094029"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>如何：在 Windows 窗体中复制像素以减少闪烁
当对简单的图形进行动画处理时，用户有时可能会遇到闪烁或其他不需要的视觉效果。 若要限制此问题的一种方法是在图形上使用"bitblt"过程。 Bitblt 是"位块传输"的颜色数据从一个源矩形的像素为单位向目标矩形的像素为单位。  
  
 使用 Windows 窗体 bitblt 通过<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法的<xref:System.Drawing.Graphics>类。 在该方法的参数，指定源和目标 （以磅为单位）、 要复制的区域的大小和用于绘制新形状的图形对象。  
  
 在下面的示例中，在窗体上绘制一个形状其<xref:System.Windows.Forms.Control.Paint>事件处理程序。 然后，<xref:System.Drawing.Graphics.CopyFromScreen%2A>方法用于复制了该形状。  
  
> [!NOTE]
>  将窗体<xref:System.Windows.Forms.Control.DoubleBuffered%2A>属性设置为`true`会使基于图形的代码中<xref:System.Windows.Forms.Control.Paint>事件是双缓冲。 使用下面的代码时，这并不会任何会造成明显的性能提升，而这是一个需要使用更复杂的图形操作代码时，请记住。  
  
## <a name="example"></a>示例  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 上面的代码运行在窗体的<xref:System.Windows.Forms.Control.Paint>事件处理程序，以便当重新绘制窗体时，仍然会保持图形。 在这种情况下，不要调用与图形相关的方法<xref:System.Windows.Forms.Form.Load>事件处理程序，因为如果窗体进行大小调整或另一个窗体被遮盖，不重绘绘制的内容。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [使用钢笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
