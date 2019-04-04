---
title: 如何：切变颜色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bb5f9043ea5bdd25e984d73d3640c80f599714e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826387"
---
# <a name="how-to-shear-colors"></a>如何：切变颜色
修剪每增加或减少到另一个颜色组件比例颜色组件。 例如，考虑红色组件加一半的蓝色组件值的转换。 在这种转换 （0.2，0.5，1） 的颜色将变为 （0.7，0.5，1）。 新的红色分量为 0.2 + (1/2)(1) = 0.7。  
  
## <a name="example"></a>示例  
 下面的示例构造<xref:System.Drawing.Image>ColorBars4.bmp 文件中的对象。 然后该代码将应用到图像中的每个像素上一段中所述的倾斜转换。  
  
 下图显示在右侧左侧上的原始映像和剪切后的图像： 
  
 ![带有彩色条带化的并排方案演示原始图像和剪切后的图像的两个方块。](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 下表列出了四个条形的颜色矢量之前和之后的倾斜转换。  
  
|原始|剪切|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，后者是 <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。 替换为`ColorBars.bmp`用的映像名称和路径在您的系统上有效。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [对图像重新着色](recoloring-images.md)
