---
title: 如何：在 Windows 窗体上绘制实心矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: e551eacf0924c9bffa802fb5d2ba8bae7c1c3a98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072022"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>如何：在 Windows 窗体上绘制实心矩形
此示例窗体上绘制实心的矩形。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>编译代码  
 不能在调用此方法<xref:System.Windows.Forms.Form.Load>事件处理程序。 不会重新绘制的内容的绘制，如果窗体进行大小调整或另一个窗体被遮盖。 若要使你自动重绘的内容，应重写<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
## <a name="robust-programming"></a>可靠编程  
 应始终调用<xref:System.IDisposable.Dispose%2A>占用系统资源，如任何对象<xref:System.Drawing.Brush>和<xref:System.Drawing.Graphics>对象。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [图形编程入门](getting-started-with-graphics-programming.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [使用钢笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ 中的画笔和实心形状](brushes-and-filled-shapes-in-gdi.md)
