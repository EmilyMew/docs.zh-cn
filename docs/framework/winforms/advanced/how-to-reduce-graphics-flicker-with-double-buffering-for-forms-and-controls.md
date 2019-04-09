---
title: 如何：通过对窗体和控件使用双缓冲来减少图形闪烁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: ef05b72b33d3f28d1811389dfae65554a1567d43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096948"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>如何：通过对窗体和控件使用双缓冲来减少图形闪烁
双缓冲使用内容缓冲来解决与多个画图操作相关的闪烁问题。 启用双缓冲后，所有画图操作会首先呈现到内存缓冲而不是屏幕上的绘图图面。 所有画图操作完成后，内存缓冲会直接复制到与之关联的绘图图面。 由于只有一个图形操作在屏幕上执行的因此消除了与复杂画图操作相关联的图像闪烁。对于大多数应用程序，默认双缓冲提供的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]将提供最佳结果。 标准 Windows 窗体控件都是双缓冲的默认值。 可以启用默认双缓冲在窗体中并编写两种方法中的控件。 你可以设置<xref:System.Windows.Forms.Control.DoubleBuffered%2A>属性设置为`true`，也可以调用<xref:System.Windows.Forms.Control.SetStyle%2A>方法以设置<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>标记，用于`true`。 这两种方法将启用默认双缓冲的窗体或控件，并提供无闪烁的图形呈现。 调用<xref:System.Windows.Forms.Control.SetStyle%2A>方法建议仅用于为其编写所有呈现代码的自定义控件。  
  
 对于更高级的双缓冲方案，如动画或高级的内存管理，可以实现自己的双缓冲逻辑。 有关详细信息，请参阅[如何：手动管理缓冲的图形](how-to-manually-manage-buffered-graphics.md)。  
  
### <a name="to-reduce-flicker"></a>若要减少闪烁  
  
-   将 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 属性设置为 `true`。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- 或 -  
  
-   调用<xref:System.Windows.Forms.Control.SetStyle%2A>方法以设置<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>标记，用于`true`。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [双缓冲图形](double-buffered-graphics.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
