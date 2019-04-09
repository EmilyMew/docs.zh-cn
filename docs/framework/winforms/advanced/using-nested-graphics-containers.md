---
title: 使用嵌套的 Graphics 容器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: 6bbf7918ccff184e597204b35aa005ab17d8d8af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104294"
---
# <a name="using-nested-graphics-containers"></a>使用嵌套的 Graphics 容器
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供了可用于临时替换或增加中状态的一部分的容器<xref:System.Drawing.Graphics>对象。 通过调用创建一个容器<xref:System.Drawing.Graphics.BeginContainer%2A>方法的<xref:System.Drawing.Graphics>对象。 您可以调用<xref:System.Drawing.Graphics.BeginContainer%2A>重复以形成嵌套的容器。 每次调用<xref:System.Drawing.Graphics.BeginContainer%2A>必须通过调用配对<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
## <a name="transformations-in-nested-containers"></a>在嵌套的容器中的转换  
 下面的示例创建<xref:System.Drawing.Graphics>对象，并在其中的容器<xref:System.Drawing.Graphics>对象。 世界转换<xref:System.Drawing.Graphics>对象是沿 x 方向平移 100 单位和 y 方向的 80 单位。 容器的世界转换是旋转 30 度。 这段代码将调用`DrawRectangle(pen, -60, -30, 120, 60)`两次。 首次调用<xref:System.Drawing.Graphics.DrawRectangle%2A>位于容器; 也就是说，调用是对的调用之间<xref:System.Drawing.Graphics.BeginContainer%2A>和<xref:System.Drawing.Graphics.EndContainer%2A>。 第二次调用<xref:System.Drawing.Graphics.DrawRectangle%2A>是在调用后<xref:System.Drawing.Graphics.EndContainer%2A>。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 在前面的代码中，从在容器内绘制的矩形转换首先按容器 （轮换） 的世界转换，然后按的世界转换<xref:System.Drawing.Graphics>对象 （转换）。 从容器外部绘制的矩形转换只能由的世界转换<xref:System.Drawing.Graphics>对象 （转换）。 下图显示了两个矩形： 
  
 ![显示嵌套的容器的图例。](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>在嵌套的容器中的剪辑  
 下面的示例演示如何嵌套的容器处理剪辑区域。 该代码会创建<xref:System.Drawing.Graphics>对象，并在其中的容器<xref:System.Drawing.Graphics>对象。 剪辑区域<xref:System.Drawing.Graphics>对象是一个矩形，该容器的剪辑区域是一个椭圆。 代码会调用两个<xref:System.Drawing.Graphics.DrawLine%2A>方法。 首次调用<xref:System.Drawing.Graphics.DrawLine%2A>是内部的容器，然后第二次调用<xref:System.Drawing.Graphics.DrawLine%2A>超出容器 (在调用<xref:System.Drawing.Graphics.EndContainer%2A>)。 第一行将被剪裁由两个剪辑区域的交集。 第二行剪辑矩形的剪辑区域只能由<xref:System.Drawing.Graphics>对象。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 下图显示了两个剪辑的行：
  
 ![显示与裁剪后的行的嵌套的容器的图例。](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 如上面的示例所示，转换和剪辑区域是在嵌套的容器中累计。 如果设置容器的世界转换和<xref:System.Drawing.Graphics>对象，这两种转换将应用于从容器内部绘制的项。 容器的转换将应用第一、 和的转换<xref:System.Drawing.Graphics>对象将第二个应用。 如果设置容器的剪辑区域和<xref:System.Drawing.Graphics>对象，从容器内部绘制的项将剪辑由两个剪辑区域的交集。  
  
## <a name="quality-settings-in-nested-containers"></a>嵌套的容器中的质量设置  
 质量设置 (<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.TextRenderingHint%2A>，等等) 中嵌套的容器不是累积的; 而是容器的质量设置临时替换的质量设置<xref:System.Drawing.Graphics>对象。 当创建新的容器时，该容器的质量设置是设置为默认值。 例如，假设您有<xref:System.Drawing.Graphics>对象的平滑模式<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 在创建容器时，在容器内的平滑模式是默认的平滑模式。 你可以随意设置平滑模式的容器，并将根据你设置了模式绘制在容器内绘制的任何项目。 绘制到的调用后的项目<xref:System.Drawing.Graphics.EndContainer%2A>将根据平滑模式绘制 (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>)，就已存在对调用之前<xref:System.Drawing.Graphics.BeginContainer%2A>。  
  
## <a name="several-layers-of-nested-containers"></a>多层嵌套的容器  
 您并不局限于一个容器中<xref:System.Drawing.Graphics>对象。 可以创建一系列容器、 每个嵌套在前面，和可以指定世界转换、 剪辑区域和每个这些嵌套容器的质量设置。 如果调用中最内部的容器内的绘制方法，将按顺序，从最内部的容器开始和结束与最外面的容器应用转换。 从最内部的容器内部绘制的项将剪辑的所有剪辑区域的交集。  
  
 下面的示例创建<xref:System.Drawing.Graphics>对象并设置其文本呈现提示为<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 该代码创建两个容器，嵌套在另一个。 外部容器的文本呈现提示设置为<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>，并且内部容器的文本呈现提示设置为<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>。 该代码绘制三个字符串： 一个来自内部容器，一个来自外部容器，一个从<xref:System.Drawing.Graphics>对象本身。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 下图显示了三个字符串。 绘制从内部容器和字符串<xref:System.Drawing.Graphics>对象进行平滑处理的抗锯齿功能。 从外部容器绘制的字符串不因为由抗锯齿平滑<xref:System.Drawing.Graphics.TextRenderingHint%2A>属性设置为<xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>。  
  
 ![显示从嵌套容器绘制的字符串的图例。](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics>
- [管理 Graphics 对象的状态](managing-the-state-of-a-graphics-object.md)
