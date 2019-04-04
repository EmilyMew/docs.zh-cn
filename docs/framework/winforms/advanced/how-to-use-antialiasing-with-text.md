---
title: 如何：对文本使用抗锯齿效果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: ffd8600c730baca54a9cbd098dd2f37ce5ecb728
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464718"
---
# <a name="how-to-use-antialiasing-with-text"></a>如何：对文本使用抗锯齿效果
*抗锯齿*指进行绘制的图形和文本，以提高它们的外观或可读性的锯齿状边缘平滑处理。 与托管[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]类，您可以呈现高质量消除锯齿的文本，以及较低质量的文本。 通常情况下，更高质量呈现花费的处理时间超过较低质量呈现。 若要设置的文本质量级别，设置<xref:System.Drawing.Graphics.TextRenderingHint%2A>的属性<xref:System.Drawing.Graphics>的元素之一<xref:System.Drawing.Text.TextRenderingHint>枚举  
  
## <a name="example"></a>示例  
 下面的代码示例绘制了两种不同的质量设置的文本。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 下图显示了示例代码的输出：  
  
 ![显示具有两个不同的质量设置文本的屏幕截图。](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的代码示例设计为使用 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅
- [使用字体和文本](using-fonts-and-text.md)
