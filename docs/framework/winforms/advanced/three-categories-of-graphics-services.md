---
title: 图形服务的三个类别
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: ccbd5e236b47d1d870c9b77cfa2b3880619cf3cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083590"
---
# <a name="three-categories-of-graphics-services"></a>图形服务的三个类别
在 Windows 窗体中的图形产品/服务划分为以下三个大类：  
  
-   二维 (2-d) 矢量图形  
  
-   图像处理  
  
-   版式  
  
## <a name="2-d-vector-graphics"></a>二维矢量图形  
 二维矢量图形是基元;如直线、 曲线和图形;由组点坐标系统上指定的。 例如，由其两个终结点，指定一条直线和矩形指定点使其左上角和一对数字使其宽度和高度的位置。 指定简单路径是由直线连接的点数组。 贝塞尔样条是指定由四个控制点的复杂的曲线。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供类和存储有关基元本身的信息的结构、 存储有关如何将绘制基元，信息的类和实际执行绘制的类。 例如，<xref:System.Drawing.Rectangle>结构存储的位置和大小的矩形;<xref:System.Drawing.Pen>类存储线条颜色、 线条宽度和线条样式; 有关的信息和<xref:System.Drawing.Graphics>类具有绘制线条、 矩形、 路径的方法和其他数字。 有几种<xref:System.Drawing.Brush>存储有关如何信息的类封闭图形和路径中将填充颜色或图案。  
  
 可将矢量图像，这是一系列图形命令，记录中图元文件。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了<xref:System.Drawing.Imaging.Metafile>类用于记录、 显示和保存图元文件。 与<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>类，可以检查存储在图元文件头中的数据。  
  
## <a name="imaging"></a>图像处理  
 某些类型的图片很难或无法显示矢量图形的方法。 例如，在工具栏按钮的图片和以图标形式显示的图片是难以指定为直线和曲线的集合。 高分辨率的数字照片的拥挤的棒球体育场，甚至更加困难，若要创建使用矢量技术。 此类型的映像存储为位图，是表示屏幕上的各个点的颜色的数字的数组。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了<xref:System.Drawing.Bitmap>用于显示、 操作和保存位图的类。  
  
## <a name="typography"></a>版式  
 版式是文本的不同的字体、 大小和样式的显示。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 为此项复杂的任务提供广泛支持。 中的新功能之一[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]子像素抗锯齿功能，它可以使文本呈现在 LCD 屏幕外观更流畅。  
  
 此外，Windows 窗体提供用于绘制文本的选项[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中的功能及其<xref:System.Windows.Forms.TextRenderer>类。  
  
## <a name="see-also"></a>请参阅

- [图形概述](graphics-overview-windows-forms.md)
- [关于 GDI+ 托管代码](about-gdi-managed-code.md)
- [使用托管图形类](using-managed-graphics-classes.md)
