---
title: 如何：使用复合模式控制 Alpha 值混合处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 1a5cf23890cd6183d92e33ec4e24f87c226e8ec3
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462859"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>如何：使用复合模式控制 Alpha 值混合处理
可能您想要创建屏幕外位图，具有以下特征：  
  
-   颜色的 alpha 值都小于 255 个。  
  
-   颜色不是 alpha 混合与每个其他的创建位图。  
  
-   显示完成的位图，位图中的颜色时，alpha 值混合处理与背景色显示设备上。  
  
 若要创建这种位图，请构造一个空白<xref:System.Drawing.Bitmap>对象，然后再构造<xref:System.Drawing.Graphics>对象基于该位图。 设置的复合模式<xref:System.Drawing.Graphics>对象传递给<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>。  
  
## <a name="example"></a>示例  
 下面的示例创建<xref:System.Drawing.Graphics>对象，基于<xref:System.Drawing.Bitmap>对象。 该代码使用<xref:System.Drawing.Graphics>对象以及两个半透明的画笔 (alpha = 160) 绘制位图上。 该代码填充红色椭圆和绿色椭圆使用半透明的画笔。 绿色椭圆重叠红色椭圆，但由于未与红色混合绿色的复合模式<xref:System.Drawing.Graphics>对象设置为<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>。  
  
 该代码在屏幕上绘制位图两次： 一次在白色背景上，一次在彩色背景上。 属于两个椭圆组成的位图中像素有 160 的 alpha 分量，因此与屏幕的背景颜色混合的省略号。  
  
 下图显示的代码示例的输出。 请注意，省略号混合和背景，但它们之间不相互进行混合。  
  
 ![与在后台，不相互混合的关系图显示省略号。](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 此代码示例包含此语句：  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 如果你希望省略号以以及在后台使用混合，更改该语句所示：  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 下图显示修改后的代码的输出。  
  
 ![图示显示省略号混合在一起并具有背景。](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，这是 <xref:System.Windows.Forms.PaintEventHandler> 的参数。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Drawing.Color.FromArgb%2A>
- [alpha 值混合处理直线和填充](alpha-blending-lines-and-fills.md)
