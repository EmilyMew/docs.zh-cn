---
title: 如何：在屏幕上绘制现有位图
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d2e06aa382bc2b01a4308f99735ca533e7a9a3ea
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653816"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>如何：在屏幕上绘制现有位图
在屏幕上，可以轻松地绘制现有映像。 首先需要创建<xref:System.Drawing.Bitmap>对象使用的位图构造函数采用一个文件名， <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>。 此构造函数接受使用几个不同的文件格式，包括 BMP、 GIF、 JPEG、 PNG 和 TIFF 图像。 创建后<xref:System.Drawing.Bitmap>对象，将其传递<xref:System.Drawing.Bitmap>对象传递给<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>对象。  
  
## <a name="example"></a>示例  
 此示例将创建<xref:System.Drawing.Bitmap>JPEG 文件中的对象，然后绘制在其左上角的位图 （60，10）。  
  
 下图显示了在指定位置绘制的位图：  
  
 ![显示的图像中的指定位置的屏幕截图。](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
