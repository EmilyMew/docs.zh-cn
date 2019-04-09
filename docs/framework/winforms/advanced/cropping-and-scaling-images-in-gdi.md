---
title: 在 GDI+ 中裁切和缩放图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183718"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>在 GDI+ 中裁切和缩放图像
可以使用<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>类可以绘制和位置矢量图像和光栅图像。 <xref:System.Drawing.Graphics.DrawImage%2A> 是重载的方法，因此有几种方法可以提供该文件使用的参数。  
  
## <a name="drawimage-variations"></a>DrawImage 变体  
 一个变体<xref:System.Drawing.Graphics.DrawImage%2A>方法接收<xref:System.Drawing.Bitmap>和一个<xref:System.Drawing.Rectangle>。 矩形指定的目标为绘制操作;也就是说，它指定在其中绘制图像的矩形。 如果目标矩形的大小不同于原始图像的大小，缩放图像以适合目标矩形。 下面的代码示例演示如何将同一图像绘制三次： 一次用于无需进行扩展，使用扩展，一次，一次用于压缩：  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 下图显示了三个图片。  
  
 ![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 某些变体<xref:System.Drawing.Graphics.DrawImage%2A>方法有源矩形参数，以及目标矩形参数。 源矩形参数指定要绘制的原始图像的部分。 目标矩形指定要在其中绘制图像的该部分的矩形。 如果目标矩形的大小不同于源矩形的大小，该图片进行缩放以适合目标矩形。  
  
 下面的代码示例演示如何构造<xref:System.Drawing.Bitmap>Runner.jpg 文件中。 使用无需进行扩展在绘制整个图像 （0，0）。 然后两次绘制的图像的一小部分： 一次使用压缩，一次使用扩展。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 下图显示了未缩放的图像和压缩和扩展的图像部分。  
  
 ![裁剪和缩放](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
