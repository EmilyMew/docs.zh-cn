---
title: 如何：在 Windows 窗体 RichTextBox 控件中显示滚动条
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 52c33239524e76bc26b9b2375578aa46bff51bf6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142553"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>如何：在 Windows 窗体 RichTextBox 控件中显示滚动条
默认情况下，Windows 窗体<xref:System.Windows.Forms.RichTextBox>控件在必要时将显示水平和垂直滚动条。 有七个可能值为<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>属性的<xref:System.Windows.Forms.RichTextBox>控件，如下表所述。  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>若要在 RichTextBox 控件中显示滚动条  
  
1.  将 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 属性设置为 `true`。 如果没有任何类型的滚动条，其中包括水平，将显示<xref:System.Windows.Forms.RichTextBox.Multiline%2A>属性设置为`false`。  
  
2.  设置<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>属性设置为适当的值的<xref:System.Windows.Forms.RichTextBoxScrollBars>枚举。  
  
    |“值”|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> （默认）|仅当文本超出宽度或长度的控件时显示和 / 或水平或垂直滚动条。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|永远不会显示任何类型的滚动条。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|显示水平滚动条仅当文本超过控件的宽度。 (，要实现这个<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>属性必须设置为`false`。)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|显示一个垂直滚动条仅当文本超过控件的高度。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|显示水平滚动条何时<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>属性设置为`false`。 在文本未超过控件的宽度时滚动条显示为灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|始终显示垂直滚动条。 滚动条的文本控件的长度不超过时显示为灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|始终显示垂直滚动条。 显示水平滚动条何时<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>属性设置为`false`。 文本不超过宽度或长度的控件时，滚动条显示为灰色。|  
  
3.  将 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 属性设置为适当的值。  
  
    |“值”|描述|  
    |-----------|-----------------|  
    |`false`|控件中的文本不会自动调整来适应控件的宽度，所以它将滚动到右侧，直到到达一个分行符。 如果您在上面选择和 / 或水平滚动条，请使用此值。|  
    |`true` （默认）|控件中的文本自动调整以适应控件的宽度。 不会出现水平滚动条。 如果选择了垂直滚动条或无、 更高版本，以显示一个或多个段落，请使用此值。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控件](richtextbox-control-windows-forms.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
