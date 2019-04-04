---
title: 管理 Graphics 对象的状态
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: a0166d2ee5a16916fdc2ece95eaf130ebd2598d5
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653777"
---
# <a name="managing-the-state-of-a-graphics-object"></a>管理 Graphics 对象的状态
<xref:System.Drawing.Graphics>类的核心是[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。 若要绘制任何内容，您可以获得<xref:System.Drawing.Graphics>对象，设置其属性，并调用其方法<xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawImage%2A>， <xref:System.Drawing.Graphics.DrawString%2A>，等等)。  
  
 下面的示例调用<xref:System.Drawing.Graphics.DrawRectangle%2A>方法的<xref:System.Drawing.Graphics>对象。 第一个参数传递给<xref:System.Drawing.Graphics.DrawRectangle%2A>方法是<xref:System.Drawing.Pen>对象。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>图形状态  
 一个<xref:System.Drawing.Graphics>对象不仅仅提供绘制方法，如<xref:System.Drawing.Graphics.DrawLine%2A>和<xref:System.Drawing.Graphics.DrawRectangle%2A>。 一个<xref:System.Drawing.Graphics>对象还维护图形状态，可以分为以下类别：  
  
-   质量设置  
  
-   转换  
  
-   剪辑区域  
  
### <a name="quality-settings"></a>质量设置  
 一个<xref:System.Drawing.Graphics>对象具有影响的项的绘制质量的多个属性。 例如，可以设置<xref:System.Drawing.Graphics.TextRenderingHint%2A>属性来指定应用于文本的抗锯齿 （如果有） 的类型。 质量会影响其他属性是<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.CompositingMode%2A>， <xref:System.Drawing.Graphics.CompositingQuality%2A>，和<xref:System.Drawing.Graphics.InterpolationMode%2A>。  
  
 下面的示例绘制一个具有平滑模式设置为两个椭圆<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>，另一个平滑模式设置为使用<xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>转换  
 一个<xref:System.Drawing.Graphics>对象维护应用到所有项的绘制的两种转换 （世界和页）<xref:System.Drawing.Graphics>对象。 任何仿射转换可以存储在世界转换。 仿射转换包括缩放、 旋转、 反射、 倾斜和转换。 可以使用页转换，缩放和更改单元 （例如，像素为单位为英寸）。 有关详细信息，请参阅[坐标系和坐标转换](coordinate-systems-and-transformations.md)。  
  
 下面的示例设置的世界和页转换<xref:System.Drawing.Graphics>对象。 世界转换设置为 30 度旋转。 设置页转换，以便坐标传递到第二个<xref:System.Drawing.Graphics.DrawEllipse%2A>将被视为毫米为单位，而不是像素为单位。 代码会两个相同调用<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。 世界转换应用于第一个<xref:System.Drawing.Graphics.DrawEllipse%2A>调用时，并 （世界和页） 这两种转换应用于第二个<xref:System.Drawing.Graphics.DrawEllipse%2A>调用。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 下图显示了两个椭圆。 请注意，30 度旋转的坐标系统 （客户端区域的左上角） 来源，而不椭圆的中心。 另请注意钢笔的宽度为 1 的第二个椭圆意味着 1 像素的第一个椭圆和 1 毫米。  
  
 ![显示两个椭圆的图示： 旋转和笔的宽度。](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>剪辑区域  
 一个<xref:System.Drawing.Graphics>对象维护应用于由，绘制的所有项的剪辑区域<xref:System.Drawing.Graphics>对象。 可以通过调用设置的剪辑区域<xref:System.Drawing.Graphics.SetClip%2A>方法。  
  
 下面的示例通过两个矩形的并集创建 plus 形区域。 该区域指定的剪辑区域为<xref:System.Drawing.Graphics>对象。 然后代码将绘制仅限于的剪辑区域内部的两行。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 下图显示了裁剪后的行：  
  
 ![图，显示受限的剪辑区域。](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>请参阅
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [使用嵌套的图形容器](using-nested-graphics-containers.md)
