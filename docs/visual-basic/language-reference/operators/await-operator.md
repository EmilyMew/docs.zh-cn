---
title: Await 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d9d50433e3bc24df7cda137a145ab3f0f0302a1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841974"
---
# <a name="await-operator-visual-basic"></a>Await 运算符 (Visual Basic)
在异步方法或 Lambda 表达式中对操作数应用 `Await` 运算符可暂停执行方法，直到所等待的任务完成。 任务表示正在进行的工作。  
  
 方法，用`Await`使用必须具有[异步](../../../visual-basic/language-reference/modifiers/async.md)修饰符。 使用 `Async` 修饰符定义并且通常包含一个或多个 `Await` 表达式的这类方法称为异步方法。  
  
> [!NOTE]
>  `Async` 和 `Await` 关键字是在 Visual Studio 2012 中引入的。 有关异步编程的介绍，请参阅[使用 Async 和 Await 的异步编程](../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
 通常情况下，应用到的任务`Await`运算符是实现的方法调用的返回值[基于任务的异步模式](https://go.microsoft.com/fwlink/?LinkId=204847)，即，<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。  
  
 在以下代码中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 返回 `getContentsTask`，一个 `Task(Of Byte())`。 当操作完成时，任务约定生成一个实际字节数组。 `Await` 运算符应用于 `getContentsTask` 以在 `SumPageSizesAsync` 中挂起执行，直到 `getContentsTask` 完成。 同时，控制权会返回给 `SumPageSizesAsync` 的调用方。 当 `getContentsTask` 完成之后，`Await` 表达式计算为字节数组。  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  有关完整示例，请参阅[演练：使用 Async 和 Await 访问 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 可以从 Microsoft 网站的[开发者代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)中下载示例。 该示例处于 AsyncWalkthrough_HttpClient 项目中。  
  
 如果 `Await` 应用于返回 `Task(Of TResult)` 的方法调用结果，则 `Await` 表达式的类型为 TResult。 如果 `Await` 应用于返回 `Task` 的方法调用结果，则 `Await` 表达式不返回值。 以下示例演示了差异。  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 `Await` 表达式或声明不阻止正在执行它的线程。 而是导致编译器在 `Await` 表达式之后，将剩下的异步方法注册为等待任务的后续部分。 控制权随后会返回给异步方法的调用方。 任务完成时，它会调用其延续任务，异步方法的执行会在暂停的位置处恢复。  
  
 `Await` 表达式只出现在由 `Async` 修饰符标记的一个立即封闭方法体或 lambda 表达式中。 术语*Await*用作关键字仅在该上下文中。 在其他位置，它会解释为标识符。 在异步方法或 lambda 表达式中，`Await`表达式中不能发生在查询表达式中，`catch`或`finally`块[尝试...Catch...最后](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)中的循环控制变量表达式语句`For`或`For Each`循环中，或正文中[SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)语句。  
  
## <a name="exceptions"></a>Exceptions  
 大多数异步方法返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。 返回任务的属性携带有关其状态和历史记录的信息，如任务是否完成、异步方法是否导致异常或已取消以及最终结果是什么。 `Await` 运算符可访问这些属性。  
  
 如果等待的任务返回异步方法导致异常，则 `Await` 运算符会重新引发异常。  
  
 如果等待的返回任务的异步方法取消，`Await` 运算符将重新引发 <xref:System.OperationCanceledException>。  
  
 处于故障状态的单个任务可以反映多个异常。  例如，任务可能是对 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 调用的结果。 等待此类任务时，等待操作仅重新引发异常之一。 但是，无法预测重新引发的异常。  
  
 异步方法中的错误处理示例，请参阅[尝试...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="example"></a>示例  
 下面的 Windows 窗体示例阐释如何在异步方法 `WaitAsynchronouslyAsync` 中使用 `Await`。 将该方法的行为与 `WaitSynchronously` 的行为进行对比。 如果没有应用 `Await` 运算符，`WaitSynchronously` 就会同步运行，而不管其定义中是否使用了 `Async` 修饰符和在主体中是否调用了 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a>请参阅

- [使用 Async 和 Await 的异步编程](../../../visual-basic/programming-guide/concepts/async/index.md)
- [演练：使用 Async 和 Await 访问 Web](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
