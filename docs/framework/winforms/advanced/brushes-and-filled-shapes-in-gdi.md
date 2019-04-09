---
title: GDI+ 中的画笔和实心形状
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 683b5966f993ac3a69c8bf7c1233b6df3d65e19a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115305"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ 中的画笔和实心形状
闭合的形状，如矩形或椭圆，由边框和内部组成。 使用笔绘制出轮廓，并使用画笔填充其内部。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了填充的绘制闭合形状内部的画笔的多个类： <xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，和<xref:System.Drawing.Drawing2D.PathGradientBrush>。 所有这些类继承自<xref:System.Drawing.Brush>类。 下图显示了以实线画笔填充矩形和椭圆用阴影画笔填充。  
  
 ![填充形状](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>纯色画笔  
 若要填充闭合的形状，你需要的实例<xref:System.Drawing.Graphics>类和一个<xref:System.Drawing.Brush>。 实例<xref:System.Drawing.Graphics>类提供了方法，如<xref:System.Drawing.Graphics.FillRectangle%2A>并<xref:System.Drawing.Graphics.FillEllipse%2A>，和<xref:System.Drawing.Brush>存储填充，如颜色和模式的特性。 <xref:System.Drawing.Brush>作为一个参数传递给填充方法。 下面的代码示例演示如何用红色纯色填充椭圆。  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  在上述示例中的类型是画笔<xref:System.Drawing.SolidBrush>，后者又继承<xref:System.Drawing.Brush>。  
  
## <a name="hatch-brushes"></a>阴影画笔  
 当使用阴影画笔填充形状时，您指定前景色、 背景色和阴影样式。 前景颜色为阴影的颜色。  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了超过 50 个阴影样式;以下插图所示的三个样式都<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>， <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>，和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。  
  
 ![填充形状](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>纹理画笔  
 使用纹理画笔，可以使用存储在位图中的模式来填充形状。 例如，假设以下图片存储在名为的磁盘文件`MyTexture.bmp`。  
  
 ![填充形状](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 下面的代码示例演示如何通过重复图片存储为填充椭圆`MyTexture.bmp`。  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 下图显示了实心的椭圆。  
  
 ![填充形状](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>渐变画笔  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了两种类型的渐变画笔： 线性和路径。 线性渐变画笔用于填充形状更改逐渐水平、 垂直移过图形或沿对角线方向的颜色。 下面的代码示例演示如何用会从蓝色变为绿色，当您从椭圆的左边缘移动到右边缘的水平渐变画笔填充椭圆。  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 下图显示了实心的椭圆。  
  
 ![填充形状](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 若要更改颜色，当您从边缘形状的中心，可以配置路径渐变画笔。  
  
 ![填充形状](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 路径渐变画笔时非常灵活。 渐变画笔用于填充中的以下图更改逐渐从中心的红色向每个顶点在三个不同的颜色的三角形。  
  
 ![填充形状](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：在 Windows 窗体上绘制实心矩形](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [如何：在 Windows 窗体上绘制实心椭圆](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
