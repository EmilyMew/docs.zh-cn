---
title: 如何：使用颜色矩阵对单色进行转换
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 66ddd85d4f841edf9cabf338fbb66a8e2dda491a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075155"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>如何：使用颜色矩阵对单色进行转换
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>用于存储和操作图像的类。 <xref:System.Drawing.Image> 和<xref:System.Drawing.Bitmap>对象存储为 32 位数字，每个像素的颜色：各 8 位红色、 绿色、 蓝色和 alpha。 每四个组件是一个介于 0 到 255 之间，其中 0 表示没有亮度，255 表示最大亮度。 Alpha 分量指定颜色的透明度：0 表示完全透明，255 表示完全不透明。  
  
 颜色向量是窗体 （红色、 绿色、 蓝色、 alpha） 4 元组。 例如，颜色向量 （0，255，0，255） 表示没有红色或蓝色，但绿色达到最大亮度不透明颜色。  
  
 表示颜色的另一个惯例使用数字 1 的最大亮度。 使用这种约定，将由向量 （0、 1、 0、 1） 表示上一段中所述的颜色。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 执行颜色转换时，请使用 1 的约定作为最大亮度。  
  
 乘以 4 × 4 矩阵的颜色矢量，您可以应用到颜色矢量线性转换 （旋转、 缩放和类似）。 但是，不能使用的 4 × 4 矩阵来执行转换 （非线性）。 如果将虚拟的第五个坐标 （例如，数字 1） 添加到每个颜色矢量，可以使用 5 × 5 矩阵来应用线性转换和翻译的任意组合。 包含跟平移的线性转换的转换称为仿射转换。  
  
 例如，假设你想要开始使用颜色 （0.2，0.0，0.4，1.0），并应用以下转换：  
  
1.  双红色组件  
  
2.  添加对红色、 绿色和蓝色组件 0.2  
  
 下面的矩阵乘法将按所列顺序执行转换的对。  
  
 ![重新着色](./media/recoloring01.gif "recoloring01")  
  
 颜色矩阵的元素进行行和列索引 （从零开始）。 例如，第五个行和第三列的矩阵 M 中的项表示由 M [4] [2]。  
  
 5 × 5 单位矩阵 （如以下插图所示） 具有的对角线上的 1 和 0 在其他地方。 如果您要乘以一个向量，颜色恒等矩阵，则不会更改颜色向量。 窗体中的颜色转换矩阵的简便方法是使用恒等矩阵来启动，稍微进行更改，生成所需的转换。  
  
 ![重新着色](./media/recoloring02.gif "recoloring02")  
  
 矩阵和转换的更多详细讨论，请参阅[坐标系和坐标转换](coordinate-systems-and-transformations.md)。  
  
## <a name="example"></a>示例  
 下面的示例将是一种颜色 （0.2，0.0，0.4，1.0） 和上一段中所述将转换应用的映像。  
  
 下图显示在右侧左侧上的原始映像和转换后的图像。  
  
 ![颜色](./media/colortrans1.png "colortrans1")  
  
 在下面的示例代码使用以下步骤进行重新着色：  
  
1.  初始化<xref:System.Drawing.Imaging.ColorMatrix>对象。  
  
2.  创建<xref:System.Drawing.Imaging.ImageAttributes>对象并将传递<xref:System.Drawing.Imaging.ColorMatrix>对象传递给<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法的<xref:System.Drawing.Imaging.ImageAttributes>对象。  
  
3.  传递<xref:System.Drawing.Imaging.ImageAttributes>对象传递给<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>对象。  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅

- [对图像重新着色](recoloring-images.md)
- [坐标系和坐标转换](coordinate-systems-and-transformations.md)
