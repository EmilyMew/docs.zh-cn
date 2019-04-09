---
title: 在 GDI+ 中绘制、定位和克隆图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: b5f98e7bdef9ff8ed0a4cd0e040cb92a31f30503
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188443"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>在 GDI+ 中绘制、定位和克隆图像
可以使用<xref:System.Drawing.Bitmap>类来加载和显示光栅图像，还可以使用<xref:System.Drawing.Imaging.Metafile>类来加载和显示矢量图像。 <xref:System.Drawing.Bitmap>并<xref:System.Drawing.Imaging.Metafile>类都继承自<xref:System.Drawing.Image>类。 若要显示矢量图像，您需要的实例<xref:System.Drawing.Graphics>类和一个<xref:System.Drawing.Imaging.Metafile>。 若要显示光栅图像，您需要的实例<xref:System.Drawing.Graphics>类和一个<xref:System.Drawing.Bitmap>。 实例<xref:System.Drawing.Graphics>类提供了<xref:System.Drawing.Graphics.DrawImage%2A>方法，用于接收<xref:System.Drawing.Imaging.Metafile>或<xref:System.Drawing.Bitmap>作为自变量。  
  
## <a name="file-types-and-cloning"></a>文件类型和克隆  
 下面的代码示例演示如何构造<xref:System.Drawing.Bitmap>Climber.jpg 文件中，并显示位图。 图像的左上角的目标点 （10，10） 中的第二个和第三个参数指定。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 下图显示图像。  
  
 ![图像示例](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 您可以构造<xref:System.Drawing.Bitmap>对象使用不同的图形文件格式：BMP、 GIF、 JPEG、 EXIF、 PNG、 TIFF 和图标。  
  
 下面的代码示例演示如何构造<xref:System.Drawing.Bitmap>中不同的文件类型的对象，然后显示位图。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap>类提供了<xref:System.Drawing.Bitmap.Clone%2A>方法可用于制作一份现有<xref:System.Drawing.Bitmap>。 <xref:System.Drawing.Bitmap.Clone%2A>方法具有可用于指定你想要复制的原始位图的部分的源矩形参数。 下面的代码示例演示如何创建<xref:System.Drawing.Bitmap>通过克隆现有的上半<xref:System.Drawing.Bitmap>。 然后绘制这两个映像。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 下图显示了两个映像。  
  
 ![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [如何：创建用于绘制的 Graphics 对象](how-to-create-graphics-objects-for-drawing.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
