---
title: 如何：对 Windows 窗体控件进行线程安全调用
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 3211df1f0e585780039471b80b5b913613ad9bbd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714003"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>如何：对 Windows 窗体控件进行线程安全调用

多线程处理可以提高性能的 Windows 窗体应用程序，但对 Windows 窗体控件的访问不是本质上是线程安全。 多线程处理可以公开你的代码非常严重且复杂的 bug。 操作控件的两个或多个线程可以迫使该控件处于不一致的状态，并会导致争用条件、 死锁，并冻结或挂起。 如果你实现多线程处理在应用中，请确保以线程安全的方式调用跨线程控件。 有关详细信息，请参阅[托管线程处理最佳做法](../../../standard/threading/managed-threading-best-practices.md)。 

有两种方法来安全地从并未创建该控件的线程调用的 Windows 窗体控件。 可以使用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法来调用在主线程，这又会调用该控件中创建一个委托。 或者，可以实现<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，它使用一个事件驱动的模型将报告结果中的后台线程完成工作。 

## <a name="unsafe-cross-thread-calls"></a>不安全的跨线程调用

它是不安全，若要直接从没有创建它的线程调用控件。 下面的代码段说明了对的不安全调用<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>控件。 `Button1_Click`事件处理程序创建一个新`WriteTextUnsafe`线程，设置主线程的<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接属性。 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Visual Studio 调试器检测到这些不安全的线程调用，通过引发<xref:System.InvalidOperationException>消息，**跨线程操作无效。控制""从其创建的线程以外的线程访问。** <xref:System.InvalidOperationException>始终不安全的跨线程调用 Visual Studio 在调试期间，发生并且可能会出现在应用运行时。 可修复此问题，但你可以通过设置禁用异常<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>属性设置为`false`。

## <a name="safe-cross-thread-calls"></a>安全的跨线程调用 

下面的代码示例演示两种方式安全地从没有创建它的线程调用的 Windows 窗体控件： 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，从主线程调用控件调用委托。 
2. 一个<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>组件，提供了一个事件驱动模型。 

在这两个示例中，后台线程处于睡眠状态一秒以模拟该线程中正在进行的工作。 

您可以生成并运行这些示例作为从.NET Framework 应用程序C#或 Visual Basic 命令行。 有关详细信息，请参阅[命令行上使用 csc.exe 生成](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[中的命令行 (Visual Basic 中) 生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。 

从.NET Core 3.0 开始，你还可以生成并运行示例作为 Windows.NET Core 应用程序从具有.NET Core Windows 窗体的文件夹 *\<文件夹名称>.csproj* 项目文件。 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>示例:使用 Invoke 方法和委托

下面的示例演示了用于确保对 Windows 窗体控件的线程安全调用的模式。 它会查询<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>属性，将该控件进行比较的创建线程 ID 以调用线程 id。 如果线程 Id 是相同的则会直接调用控件。 如果线程 Id 不相同，则会调用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>从主线程，这使得对控件的实际调用的委托的方法。

`SafeCallDelegate`允许设定<xref:System.Windows.Forms.TextBox>控件的<xref:System.Windows.Forms.TextBox.Text%2A>属性。 `WriteTextSafe`方法查询<xref:System.Windows.Forms.Control.InvokeRequired%2A>。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>将返回`true`，`WriteTextSafe`传递`SafeCallDelegate`到<xref:System.Windows.Forms.Control.Invoke%2A>进行实际调用控件的方法。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>将返回`false`，`WriteTextSafe`设置<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接。 `Button1_Click`事件处理程序将创建新线程并运行`WriteTextSafe`方法。 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>示例:使用 BackgroundWorker 事件处理程序

方便地实现多线程是使用<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>组件，使用事件驱动模型。 后台线程运行<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>事件，不与主线程进行交互。 主线程运行<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件处理程序，可以调用主线程的控件。

若要通过使用调用线程安全<xref:System.ComponentModel.BackgroundWorker>，在后台线程来执行工作，创建一种方法，并将其绑定到<xref:System.ComponentModel.BackgroundWorker.DoWork>事件。 在主线程来报告后台工作，结果中创建另一种方法并将其绑定到<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>或<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。 若要启动后台线程，请调用<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。 

该示例使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件处理程序设置<xref:System.Windows.Forms.TextBox>控件的<xref:System.Windows.Forms.TextBox.Text%2A>属性。 有关使用示例<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，请参阅<xref:System.ComponentModel.BackgroundWorker>。 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>请参阅

- <xref:System.ComponentModel.BackgroundWorker>
- [如何：在后台运行操作](how-to-run-an-operation-in-the-background.md)
- [如何：实现使用后台操作的窗体](how-to-implement-a-form-that-uses-a-background-operation.md)
- [开发自定义 Windows 窗体控件与.NET Framework](developing-custom-windows-forms-controls.md)
