---
title: 如何：创建线性渐变
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 540b6d422be5d5c0898f019592a755258145d14d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125016"
---
# <a name="how-to-create-a-linear-gradient"></a>如何：创建线性渐变
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了水平、 垂直，和对角线线性渐变。 默认情况下，线性渐变中的颜色均匀地变化。 以便以非均匀方式将颜色更改，但是，可以自定义线性渐变。  
  
 下面的示例填充直线、 椭圆和水平线性渐变画笔的矩形。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>构造函数接收四个参数： 两个点和两种颜色。 第一个点 （0，10） 程序与第一种颜色 （红色），并且第二个点 （200，10） 与第二种颜色 （蓝色） 相关联。 如您所料的从绘制的线条 （0，10） 到 （200，10） 由红色变为蓝色逐渐更改。  
  
 中的点 （50，10） 和 （200，10） 10 秒并不重要。 重要的是，两个点的第二个坐标相同 — 连接二者的线是水平。 椭圆和矩形也逐渐更改由红色变为蓝色因为是由从 0 到 200 的水平坐标。  
  
 下图显示线条、 椭圆和矩形。 请注意，图的颜色渐变本身可根据重复的水平坐标增加到 200 以上。  
  
 ![线性渐变](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>若要使用水平线性渐变  
  
-   将不透明红色和不透明蓝色分别作为第三个和第四个参数传递。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 在前面的示例中，颜色组件以线性方式更改为 0 的水平坐标从移动到 200 的水平坐标。 例如，其第一个坐标是 0 到 200 之间的中间位置的点将有一个介于 0 和 255 之间的中间位置的蓝色组件。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可以调整一种颜色在某条边的渐变的其他不同的方式。 假设你想要创建从黑色更改为根据下表的红色渐变画笔。  
  
|水平坐标|RGB 组件|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 请注意，红色组件以半强度时，水平坐标是只有 20%的从 0 到 200 的方法。  
  
 下面的示例设置<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A>属性的<xref:System.Drawing.Drawing2D.LinearGradientBrush>将三个相对亮度与三个相对位置相关联的对象。 如前面的表中所示相对强度是 0.5 的与 0.2 的相对位置相关联。 该代码填充椭圆和矩形使用渐变画笔。  
  
 下图显示得到的椭圆和矩形。  
  
 ![线性渐变](./media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>若要自定义线性渐变  
  
-   将不透明的黑色和不透明红色分别作为第三个和第四个参数传递。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 在上述示例中的渐变的方向是水平;也就是说，颜色逐渐变化沿任意水平行移动。 此外可以定义垂直渐变和对角线渐变。  
  
 下面的示例将点 （0，0） 和 （200，100） 传递给<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>构造函数。 与之关联的颜色蓝色 （0，0），并与之关联的绿色 （200，100）。 使用线性渐变画笔填充行 （使用笔宽度为 10） 和一个椭圆。  
  
 下图显示了在行和椭圆。 请注意，在椭圆更改颜色逐渐沿任意移动行的是并行的行通过传递到 （0，0） 和 （200，100）。  
  
 ![线性渐变](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>若要创建对角线线性渐变  
  
-   传入的不透明的蓝色和不透明绿色作为第三个和第四个参数，分别。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>请参阅

- [使用渐变画笔填充形状](using-a-gradient-brush-to-fill-shapes.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
