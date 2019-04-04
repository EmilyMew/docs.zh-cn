---
title: 如何：通过避免自动缩放改善性能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: 8580bd2212a025edddada9e47b0dc2b6195b53c7
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653790"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>如何：通过避免自动缩放改善性能
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 在绘制时，这会降低性能，可能会自动缩放图像。 或者，可以控制图像缩放通过将传递到目标矩形的尺寸<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
 例如，以下调用到<xref:System.Drawing.Graphics.DrawImage%2A>方法指定的左上角 （50，30），但未指定目标矩形。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 虽然这是最简单版本的<xref:System.Drawing.Graphics.DrawImage%2A>方法所需的参数个数不一定是最有效。 如果使用的分辨率[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]（通常每英寸 96 点） 不同于存储中的分辨率<xref:System.Drawing.Image>对象，则<xref:System.Drawing.Graphics.DrawImage%2A>方法会将图像缩放。 例如，假设<xref:System.Drawing.Image>对象具有宽度为 216 像素和存储的水平分辨率值为 72 以每英寸点数。 因为 216/72 为 3，<xref:System.Drawing.Graphics.DrawImage%2A>会将图像缩放以使其具有最适宜的分辨率的每英寸 96 点 3 英寸的宽度。 也就是说，<xref:System.Drawing.Graphics.DrawImage%2A>将显示图像的宽度为 96 x 3 = 288 条的像素为单位。  
  
 即使您的屏幕分辨率每英寸 96 点从不同[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]将可能横向图像，像屏幕分辨率每英寸 96 点。 这是因为[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<xref:System.Drawing.Graphics>对象所关联的设备上下文，以及何时[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]屏幕分辨率，结果的设备上下文通常为 96，而不考虑实际屏幕分辨率的查询。 通过指定目标矩形中的自动缩放，可以避免<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
## <a name="example"></a>示例  
 下面的示例绘制两次相同的映像。 在第一种情况下，未指定的宽度和高度的目标矩形，并自动缩放图像。 在第二种情况下，指定的宽度和高度 （以像素为单位） 的目标矩形是相同的宽度和原始图像的高度。 下图显示了两次呈现的图像：  
  
 ![显示与缩放后的纹理的图像的屏幕截图。](./media/how-to-improve-performance-by-avoiding-automatic-scaling/two-scaled-texture-images.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。 将映像名称和在您的系统都有效的路径替换为 Texture.jpg。  
  
## <a name="see-also"></a>请参阅
- [图像、位图和图元文件](images-bitmaps-and-metafiles.md)
- [使用图像、位图、图标和图元文件](working-with-images-bitmaps-icons-and-metafiles.md)
