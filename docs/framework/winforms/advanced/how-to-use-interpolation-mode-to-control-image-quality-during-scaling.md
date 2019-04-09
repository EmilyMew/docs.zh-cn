---
title: 如何：在缩放期间使用内插模式控制图像质量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 75f5077c2d969f026a28834144c219f289843dd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080977"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>如何：在缩放期间使用内插模式控制图像质量
内插模式<xref:System.Drawing.Graphics>对象的影响方式[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]缩放 （拉伸和收缩） 映像。 <xref:System.Drawing.Drawing2D.InterpolationMode>枚举定义多个内插模式，其中一些以下列表所示：  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 拉伸图像，原始图像中的每个像素必须映射到一个组中可查看大图像的像素。 若要缩小图像，组中的原始图像的像素必须映射到较小的图像中单个像素。 执行这些映射的算法的有效性确定缩放的图像的质量。 生成高质量缩放的图像的算法往往需要进行更多的处理时间。 在上述列表中，<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>是最低质量模式和<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>是最高质量的模式。  
  
 若要设置的内插模式，将分配的成员<xref:System.Drawing.Drawing2D.InterpolationMode>枚举<xref:System.Drawing.Graphics.InterpolationMode%2A>属性的<xref:System.Drawing.Graphics>对象。  
  
## <a name="example"></a>示例  
 下面的示例绘制一个图像，然后对具有三种不同内插模式的图像进行收缩。  
  
 下图显示了原始图像和三个较小的图像。  
  
 ![显示具有各种内插设置的图像的屏幕截图。](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅

- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
