---
title: 如何：使用 Windows 窗体 RichTextBox 控件设置缩进、悬挂缩进和点符段落
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4cb9b351b5ed1ab9cd05be0763d967000791fb46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140642"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>如何：使用 Windows 窗体 RichTextBox 控件设置缩进、悬挂缩进和点符段落
Windows 窗体<xref:System.Windows.Forms.RichTextBox>控件具有许多选项用于设置所显示的文本的格式。 您可以通过设置所选的段落格式为项目符号列表<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>属性。 此外可以使用<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>， <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>，和<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>属性设置相对于左和右边缘的控件和其他文本行的左边的缘的段落的缩进值。  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>将段落的格式设置为项目符号列表  
  
1.  将 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 属性设置为 `true`。  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>缩进段落  
  
1.  设置<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>属性设置为一个整数，表示以像素为单位的控件的左边的缘与文本的左边的缘之间的距离。  
  
2.  设置<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>属性设置为一个整数，表示以像素为单位的段落中的文本的第一个行的左边的缘和同一段落中后面的行的左边的缘之间的距离。 值<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>属性仅应用于段落中第一行下面换行。  
  
3.  设置<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>属性设置为一个整数，表示以像素为单位的控件的右边缘和文本的右边缘之间的距离。  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  所有上述属性均影响包含所选文本的任何段落，还会影响在当前插入点之后键入的文本。 例如，当用户在段落中选择一个词然后调整缩进时，新的设置将应用于包含该词的整个段落，还会应用于随后在所选段落之后输入的任何段落。 有关以编程方式选择文本的信息，请参阅<xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控件](richtextbox-control-windows-forms.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
