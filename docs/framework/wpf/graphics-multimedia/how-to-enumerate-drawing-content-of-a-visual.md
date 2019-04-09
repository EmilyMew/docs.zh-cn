---
title: 如何：枚举视觉对象的绘图内容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107999"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>如何：枚举视觉对象的绘图内容
<xref:System.Windows.Media.Drawing>对象提供用于枚举的内容的对象模型<xref:System.Windows.Media.Visual>。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法来检索<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>并枚举该值。  
  
> [!NOTE]
>  当枚举视觉对象的内容时，就在检索<xref:System.Windows.Media.Drawing>对象和表示形式呈现数据作为矢量图形指令列表不基础。 有关详细信息，请参阅 [WPF 图形呈现概述](wpf-graphics-rendering-overview.md)。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Drawing 对象概述](drawing-objects-overview.md)
- [WPF 图形呈现疑难解答](wpf-graphics-rendering-overview.md)
