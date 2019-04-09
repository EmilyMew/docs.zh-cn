---
title: 如何：在窗体一级处理键盘输入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: fbb6587dde53592a94887c1ea19562e06c15afe3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135156"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>如何：在窗体一级处理键盘输入
Windows 窗体能够在消息到达控件之前处理窗体级别的键盘消息。 本主题演示如何完成此任务。  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>处理窗体级别的键盘消息  
  
-   处理启动窗体的 <xref:System.Windows.Forms.Control.KeyPress> 或 <xref:System.Windows.Forms.Control.KeyDown> 事件，并将该窗体的 <xref:System.Windows.Forms.Form.KeyPreview%2A> 属性设置为 `true`，以便在键盘消息到达窗体上的任何控件之前接收到键盘消息。 以下代码示例通过检测所有的数字键以及使用“1”、“4”和“7”来处理 <xref:System.Windows.Forms.Control.KeyPress> 事件。  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>示例  
 以下代码示例是上述示例的整个应用程序。 此应用程序包括一个 <xref:System.Windows.Forms.TextBox> 和几个允许你从 <xref:System.Windows.Forms.TextBox> 中移动焦点的控件。 显示剩余键时，主要 <xref:System.Windows.Forms.Form> 的 <xref:System.Windows.Forms.Control.KeyPress> 事件使用“1”、“4”和“7”，而 <xref:System.Windows.Forms.TextBox> 的 <xref:System.Windows.Forms.Control.KeyPress> 事件使用“2”、“5”和“8”。 比较在 <xref:System.Windows.Forms.TextBox> 具有焦点时按数字键的 <xref:System.Windows.Forms.MessageBox> 输出以及在焦点位于其他控件上时按数字键的 <xref:System.Windows.Forms.MessageBox> 输出。  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  

## <a name="see-also"></a>请参阅

- [Windows 窗体应用程序中的键盘输入](keyboard-input-in-a-windows-forms-application.md)
