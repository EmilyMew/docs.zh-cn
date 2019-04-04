---
title: 如何：裁剪和缩放图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: ff0567dca0fd86736e02a9dd827ec15df8bf2df8
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654492"
---
# <a name="how-to-crop-and-scale-images"></a>如何：裁剪和缩放图像
<xref:System.Drawing.Graphics>类提供了若干<xref:System.Drawing.Graphics.DrawImage%2A>方法，其中一些具有可用于裁剪和缩放图像的源和目标矩形参数。  
  
## <a name="example"></a>示例  
 下面的示例构造<xref:System.Drawing.Image>从磁盘文件 Apple.gif 对象。 该代码在其原始大小绘制整个 apple 图像。 然后，代码调用<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>对象大于原始 apple 映像的目标矩形中绘制 apple 图像的一部分。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法确定 apple 通过查看源矩形，由第三个、 第四，指定第五和第六个参数绘制的哪个部分。 在这种情况下，在 apple 要裁剪成其宽度的 75%和 75%的窗体的高度。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法确定绘制裁剪后的 apple 的位置和大小以便裁剪后的 apple 通过查看目标矩形，即指定的第二个参数。 在这种情况下，目标矩形是更广的 30%，比原始图像高度的 30%。  
  
 下图显示了原始 apple 和缩放、 裁剪 apple。  
  
 ![原始图像和裁剪的同一映像的屏幕截图。](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。 请务必替换`Apple.gif`与图像文件名称和在您的系统都有效的路径。  
  
## <a name="see-also"></a>请参阅
- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
