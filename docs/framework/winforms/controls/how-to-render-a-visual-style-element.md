---
title: 如何：呈现视觉样式元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 44218ee1f3879a3f9ac5a1e1b049c28a5463820e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099828"
---
# <a name="how-to-render-a-visual-style-element"></a>如何：呈现视觉样式元素
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空间公开了<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>对象，后者表示 Windows 用户界面 (UI) 元素支持的视觉样式。 本主题演示如何使用<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>类来呈现<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>，它表示**注销**并**关机**开始菜单的按钮。  
  
### <a name="to-render-a-visual-style-element"></a>若要呈现的视觉样式元素  
  
1.  创建<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>并将其设置为想要绘制的元素。 请注意，使用<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType>属性和<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType>方法;<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A>构造函数将引发异常，如果禁用了视觉样式，或者元素未定义。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  调用<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A>方法来呈现元素<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>当前表示。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   自定义控件派生自<xref:System.Windows.Forms.Control>类。  
  
-   一个<xref:System.Windows.Forms.Form>承载自定义控件。  
  
-   对引用<xref:System?displayProperty=nameWithType>， <xref:System.Drawing?displayProperty=nameWithType>， <xref:System.Windows.Forms?displayProperty=nameWithType>，和<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空间。  
  
## <a name="see-also"></a>请参阅

- [使用视觉样式呈现控件](rendering-controls-with-visual-styles.md)
