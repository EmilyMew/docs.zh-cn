---
title: 坐标系类型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089297"
---
# <a name="types-of-coordinate-systems"></a>坐标系类型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用三个坐标空间： 世界、 页和设备。 用于建模对特定图形世界坐标世界坐标，将传递给.NET Framework 中的方法的坐标。 页坐标是指由绘图图面，如窗体或控件使用的坐标系统。 设备坐标是由物理设备上，如屏幕或纸张进行绘制的坐标。 进行调用时`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，将传递给点<xref:System.Drawing.Graphics.DrawLine%2A>方法 —`(0, 0)`和`(160, 80)`— 世界坐标空间中。 之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以在屏幕上绘制行中，通过一系列的转换传递的坐标。 一个转换，名为世界转换中，将世界坐标转换为页面坐标和另一个转换，调用页转换，将页面坐标转换为设备坐标。  
  
## <a name="transforms-and-coordinate-systems"></a>转换和坐标系  
 假设你想要使用的工作区而不是左上角的正文中原点的坐标系。 例如，假设你需要为 100 像素从工作区左边缘和从客户端区域的顶部 50 像素的原点。 下图显示了这样的坐标系统。  
  
 ![坐标系](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 进行调用时`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，获取显示在下图中的行。  
  
 ![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 您在三个坐标空间中的终结点的坐标是行的按如下所示：  
  
|||  
|-|-|  
|世界|（0，0） 到 （160，80）|  
|页面|（100，50） 到 （260、 130）|  
|设备|（100，50） 到 （260、 130）|  
  
 请注意页面坐标空间的客户端区域，则左上角的原点此属性始终为这种情况。 此外请注意，因为度量值的单位是像素，设备坐标相同的页坐标。 如果您设置的度量单位为像素 （例如，英寸为单位） 以外，设备坐标将不同于页坐标。  
  
 世界转换，将世界坐标映射到页坐标，会保留在<xref:System.Drawing.Graphics.Transform%2A>属性的<xref:System.Drawing.Graphics>类。 在上述示例中，世界转换是沿 x 方向平移 100 个单位，50 个单位，在 y 方向。 下面的示例设置的世界转换<xref:System.Drawing.Graphics>对象，然后使用该<xref:System.Drawing.Graphics>对象来绘制在上图中显示的行：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 页转换将页坐标映射到设备坐标。 <xref:System.Drawing.Graphics>类提供了<xref:System.Drawing.Graphics.PageUnit%2A>和<xref:System.Drawing.Graphics.PageScale%2A>操作页转换的属性。 <xref:System.Drawing.Graphics>类还提供了两个只读属性，<xref:System.Drawing.Graphics.DpiX%2A>和<xref:System.Drawing.Graphics.DpiY%2A>，用于检查每英寸点数的显示设备的水平和垂直点。  
  
 可以使用<xref:System.Drawing.Graphics.PageUnit%2A>属性的<xref:System.Drawing.Graphics>类，以指定的像素以外的度量单位。  
  
> [!NOTE]
>  不能设置<xref:System.Drawing.Graphics.PageUnit%2A>属性设置为<xref:System.Drawing.GraphicsUnit.World>，因为这不是物理单元，将导致异常。  
  
 下面的示例绘制一条线从 （0，0） 到 （2，1），其中的点 （2，1） 为 2 英寸向右和向下从点 （0，0） 的 1 英寸：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  如果未指定笔的宽度，在构造笔时，前面的示例将绘制一英寸宽的线条。 可以在第二个参数中指定钢笔的宽度<xref:System.Drawing.Pen>构造函数：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 如果我们假设显示设备的 96 点 / 英寸沿水平方向和垂直方向中每英寸 96 点，前面示例中的行的终结点将具有三个坐标空间中的以下坐标：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|页面|（0，0） 到 （2，1）|  
|设备|(0，0，为 （192，96）|  
  
 请注意，因为世界坐标系原点位于工作区的左上角，页面坐标与世界坐标相同。  
  
 你可以组合的世界和页转换，以实现各种效果。 例如，假设你想要使用英寸作为度量单位和所需的坐标系统为 2 英寸距左边缘的工作区和从客户端区域顶部的 1/2 英寸的来源。 下面的示例设置的世界和页转换<xref:System.Drawing.Graphics>对象，然后绘制行从 （0，0） 到 （2，1）：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 下图显示的行和坐标系统。  
  
 ![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 如果我们假设显示设备的 96 点 / 英寸沿水平方向和垂直方向中每英寸 96 点，前面示例中的行的终结点将具有三个坐标空间中的以下坐标：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|页面|（2，0.5） 到 （4，1.5）|  
|设备|（192，48） 到 （384，第 144）|  
  
## <a name="see-also"></a>请参阅

- [坐标系和坐标转换](coordinate-systems-and-transformations.md)
- [转换的矩阵表示形式](matrix-representation-of-transformations.md)
