---
title: 如何：创建只读文本框 （Windows 窗体）
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: be85eedf272e596ceb10e7510b8c99ce6aed0727
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130723"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>如何：创建只读文本框 （Windows 窗体）
可以将可编辑的 Windows 窗体文本框中转换为只读的控件。 例如，在文本框中可能显示一个值，通常编辑，但可能目前，由于应用程序的状态。  
  
### <a name="to-create-a-read-only-text-box"></a>若要创建只读文本框  
  
1.  设置<xref:System.Windows.Forms.TextBox>控件的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>属性设置为`true`。 属性设置为`true`，用户仍可以向下滚动并突出文本在文本框中显示但不允许更改。 一个**副本**命令将一个文本框中, 正常运行，但**剪切**并**粘贴**命令不是。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>属性只影响在运行时的用户交互。 您可以仍更改文本框的内容以编程方式在运行时通过更改<xref:System.Windows.Forms.TextBox.Text%2A>属性文本框的。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
