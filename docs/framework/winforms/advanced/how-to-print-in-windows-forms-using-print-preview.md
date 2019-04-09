---
title: 如何：使用打印预览在 Windows 窗体中进行打印
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 48391465bf199f8a212a575c64227958385eeae8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073606"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a>如何：使用打印预览在 Windows 窗体中进行打印
除了打印服务之外，Windows 窗体编程中通常还提供打印预览。 要将打印预览服务添加到你的应用程序有一个简单的方法，就是将 <xref:System.Windows.Forms.PrintPreviewDialog> 控件与用于打印文件的 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件处理逻辑结合使用。  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a>若要预览带有 PrintPreviewDialog 控件的文本文档  
  
1.  向你的窗体添加 <xref:System.Windows.Forms.PrintPreviewDialog>、 <xref:System.Drawing.Printing.PrintDocument>和两个字符串。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  为你想要打印的文档设置 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 属性，然后打开并读取文档内容到之前添加的字符串。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  就像你为了打印文件所执行的操作那样，在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件处理程序中使用 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 类的 <xref:System.Drawing.Printing.PrintPageEventArgs> 属性和文件内容来计算每页行数并呈现文档的内容。 绘制完每一页后，检查它是否是最后一页，并相应地设置 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 属性。 引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，直到 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 为 `false`。 当文档已完成呈现时，将字符串重置为已呈现。 此外，确保 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件与其事件处理方法关联。  
  
    > [!NOTE]
    >  如果已在应用程序中实现打印，你可能已完成了步骤 2 和 3。  
  
     在下列代码示例中，事件处理程序用于打印“testPage.txt”文件的内容，所用字体与窗体上使用的字体相同。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  在窗体上，将 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> 控件的 <xref:System.Windows.Forms.PrintPreviewDialog> 属性设置为 <xref:System.Drawing.Printing.PrintDocument> 组件。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  调用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 控件上的 <xref:System.Windows.Forms.PrintPreviewDialog> 方法。 你通常会从一个按钮的 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 事件处理方法调用 <xref:System.Windows.Forms.Control.Click> 。 调用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 会引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，并将输出呈现到 <xref:System.Windows.Forms.PrintPreviewDialog> 控件。 当用户单击对话框上的打印按钮时，会再次引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，将输出发送至打印机而不是预览对话框。 这就是在步骤 3 中该字符串在呈现过程结尾重置的原因。  
  
     下列代码示例显示了窗体上一个按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理方法。 此事件处理方法调用方法来读取文档，并显示打印预览对话框。  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Windows.Forms 和 System.Drawing 程序集的引用。  
  
-   Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  
  
## <a name="see-also"></a>请参阅

- [如何：打印 Windows 窗体中的多页文本文件](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows 窗体打印支持](windows-forms-print-support.md)
- [Windows 窗体中的更加安全的打印](../more-secure-printing-in-windows-forms.md)
