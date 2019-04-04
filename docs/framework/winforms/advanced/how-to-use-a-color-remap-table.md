---
title: 如何：使用颜色重新映射表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 73f4f19229a31266b406214e93e2b59acd343ca2
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463886"
---
# <a name="how-to-use-a-color-remap-table"></a>如何：使用颜色重新映射表
重新映射是转换颜色重新映射表根据图像中的颜色的过程。 颜色重新映射表是一个数组<xref:System.Drawing.Imaging.ColorMap>对象。 每个<xref:System.Drawing.Imaging.ColorMap>数组中的对象具有<xref:System.Drawing.Imaging.ColorMap.OldColor%2A>属性和一个<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>属性。  
  
 当[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]绘制一个图像，图像的每个像素与旧颜色数组进行比较。 如果像素的颜色与旧的颜色相匹配，其颜色更改为相应的新颜色。 仅对呈现更改的颜色，图像本身的颜色值 (存储在<xref:System.Drawing.Image>或<xref:System.Drawing.Bitmap>对象) 将不会更改。  
  
 若要绘制重新映射的图像，初始化数组的<xref:System.Drawing.Imaging.ColorMap>对象。 传递到该数组<xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>对象，并将传递<xref:System.Drawing.Imaging.ImageAttributes>对象传递给<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>对象。  
  
## <a name="example"></a>示例  
 下面的示例创建<xref:System.Drawing.Image>RemapInput.bmp 文件中的对象。 代码将创建包含单个颜色重新映射表<xref:System.Drawing.Imaging.ColorMap>对象。 <xref:System.Drawing.Imaging.ColorMap.OldColor%2A>的属性`ColorRemap`对象为红色，和<xref:System.Drawing.Imaging.ColorMap.NewColor%2A>属性显示为蓝色。 映像是在不重新映射的情况下绘制一次，一次用于重新映射。 重新映射过程会更改所有红色的像素为蓝色。  
  
 下图显示在右侧左侧上的原始映像和重新映射的图像。  
  
 ![显示原始图像和重新映射的图像的屏幕截图。](./media/how-to-use-a-color-remap-table/original-image-remap-colors.png)  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，后者是 <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。  
  
## <a name="see-also"></a>请参阅
- [对图像重新着色](recoloring-images.md)
- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
