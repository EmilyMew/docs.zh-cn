---
title: 如何：使用 OpenFileDialog 组件打开文件
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 5781543a61d77ef8f0658e95759c57fdb77cfc4f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723083"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>如何：使用 OpenFileDialog 打开的文件 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>组件打开 Windows 对话框中浏览并选择文件。 若要打开和读取所选的文件，可以使用<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>方法，或创建的实例<xref:System.IO.StreamReader?displayProperty=nameWithType>类。 以下示例演示这两种方法。 

在.NET Framework 中，要获取或设置<xref:System.Windows.Forms.FileDialog.FileName%2A>属性需要的特权等级授予通过<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>类。 示例运行<xref:System.Security.Permissions.FileIOPermission>权限检查，并可以在部分信任上下文中运行的情况下引发因特权不足而异常。 有关详细信息，请参阅[代码访问安全性基础知识](../../misc/code-access-security-basics.md)。

您可以生成并运行这些示例作为从.NET Framework 应用程序C#或 Visual Basic 命令行。 有关详细信息，请参阅[命令行上使用 csc.exe 生成](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[中的命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。 

从.NET Core 3.0 开始，你还可以生成并运行示例作为 Windows.NET Core 应用程序从具有.NET Core Windows 窗体的文件夹 *\<文件夹名称>.csproj* 项目文件。 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>示例:为流使用 StreamReader 读取文件  
  
下面的示例使用 Windows 窗体<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Click>事件处理程序以打开<xref:System.Windows.Forms.OpenFileDialog>与<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。 当用户选择一个文件并选择后**确定**，实例<xref:System.IO.StreamReader>类读取文件，并在窗体的文本框中显示其内容。 有关从文件流读取的详细信息，请参阅<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>和<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>示例:打开文件中使用 OpenFile 筛选选定内容 

下面的示例使用<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Click>事件处理程序打开<xref:System.Windows.Forms.OpenFileDialog>与筛选器，显示仅文本文件。 当用户选择一个文本文件，并选择后**确定**，则<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法用于在记事本中打开该文件。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 组件](openfiledialog-component-windows-forms.md)
