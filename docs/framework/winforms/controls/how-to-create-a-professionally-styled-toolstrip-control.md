---
title: 如何：创建采用专业样式的 ToolStrip 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6da6e113867efed79dfcd02f3b89ee1f9ae13c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104581"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>如何：创建采用专业样式的 ToolStrip 控件
可以通过编写自己的派生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 类型的类，赋予应用程序的 <xref:System.Windows.Forms.ToolStrip> 控件一个专业的外观和行为（外观和感受）。  
  
 没有对此功能在 Visual Studio 中的广泛支持。  
  
 请参阅[演练：创建具有专业样式的 ToolStrip 控件](walkthrough-creating-a-professionally-styled-toolstrip-control.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何使用<xref:System.Windows.Forms.ToolStrip>控件，创建复合控件，以模拟**导航窗格**Microsoft Outlook® 提供的。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  另请参阅[演练：创建具有专业样式的 ToolStrip 控件](walkthrough-creating-a-professionally-styled-toolstrip-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip 控件](toolstrip-control-windows-forms.md)
- [如何：向窗体提供标准菜单项](how-to-provide-standard-menu-items-to-a-form.md)
