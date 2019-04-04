---
title: 取消一个异步任务或一组任务 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: deb469f2c083870fc96c9217fa862d189629df1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834980"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>取消一个异步任务或一组任务 (Visual Basic)
如果不想等待异步应用程序完成，可以设置一个按钮用来取消它。 通过遵循本主题中的示例，可以为下载一个或一组网站内容的应用程序添加一个取消按钮。  
  
 这些示例使用用户界面的[微调异步应用程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)描述。  
  
> [!NOTE]
>  若要运行该示例，计算机上必须安装有 Visual Studio 2012 或更高版本和 .NET Framework 4.5 或更高版本。  
  
## <a name="BKMK_CancelaTask"></a>取消任务  
 第一个示例将“取消”按钮与单个下载任务关联。 如果在应用程序下载内容时选择按钮，下载将取消。  
  
### <a name="downloading-the-example"></a>下载示例  
 若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。  
  
1.  解压缩下载的文件，然后启动 Visual Studio。  
  
2.  在菜单栏上，依次选择 **“文件”**、 **“打开”** 和 **“项目/解决方案”**。  
  
3.  在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningVB 的解决方案 (.sln) 文件。  
  
4.  在“解决方案资源管理器”中，打开 “CancelATask” 项目的快捷菜单，然后选择“设为启动项目”。  
  
5.  选择 F5 键运行该项目。  
  
     选择 Ctrl+F5 键运行该项目，而不进行调试。  
  
 如果不想下载项目，可以查看本主题末尾处的 MainWindow.xaml.vb 文件。  
  
### <a name="building-the-example"></a>生成示例  
 下列更改将“取消”按钮添加到下载网站的应用程序中。 如果不想下载或生成示例，则可在本主题末尾的“完整示例”部分查看最终产品。 星号标记了代码中的更改。  
  
 要自行生成示例，请按“下载示例”部分的说明逐步操作，选择“StarterCode”而不是“CancelATask”作为“启动项目”。  
  
 然后将下列更改添加到该项目的 MainWindow.xaml.vb 文件。  
  
1.  声明一个 `CancellationTokenSource` 变量 `cts`，它作用于所有访问它的方法。  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  为“取消”按钮添加以下事件处理程序。 用户请求取消时，事件处理程序使用 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法通知 `cts`。  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  为“启动”按钮 `startButton_Click` 在事件处理程序中进行下列更改。  
  
    -   实例化 `CancellationTokenSource`、`cts`。  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   在 `AccessTheWebAsync` 调用中（该操作下载指定网站的内容），将 `cts` 的 <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> 属性作为参数发送。 如果请求取消，则 `Token` 属性传播消息。 如果用户选择取消下载操作，请添加显示消息的 catch 块。 下列代码显示这些更改。  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  在 `AccessTheWebAsync` 中，使用 <xref:System.Net.Http.HttpClient> 类型中 `GetAsync` 方法的 <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 重载来下载网站内容。 将 `ct`（`AccessTheWebAsync` 的 <xref:System.Threading.CancellationToken> 参数）作为第二个参数传递。 如果用户选择“取消”按钮，则令牌携带消息。  
  
     下列代码显示 `AccessTheWebAsync` 中的更改。  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  如果不取消该程序，它将生成以下输出。  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     如果在程序完成下载内容前，选择“取消”按钮，则程序将生成以下输出。  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
## <a name="BKMK_CancelaListofTasks"></a>取消任务列表  
 通过将相同的 `CancellationTokenSource` 示例与每个任务关联，可以扩展先前的示例，从而取消多个任务。 如果选择“取消”按钮，则将取消所有尚未完成的任务。  
  
### <a name="downloading-the-example"></a>下载示例  
 若要下载完整的 Windows Presentation Foundation (WPF) 项目，请参阅 [Async Sample:Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）。  
  
1.  解压缩下载的文件，然后启动 Visual Studio。  
  
2.  在菜单栏上，依次选择 **“文件”**、 **“打开”** 和 **“项目/解决方案”**。  
  
3.  在“打开项目”对话框中，打开保存已解压的示例代码的文件夹，然后打开 AsyncFineTuningVB 的解决方案 (.sln) 文件。  
  
4.  在“解决方案资源管理器”中，打开 “CancelAListOfTasks” 项目的快捷菜单，然后选择“设为启动项目”。  
  
5.  选择 F5 键运行该项目。  
  
     选择 Ctrl+F5 键运行该项目，而不进行调试。  
  
 如果不想下载项目，可以查看本主题末尾处的 MainWindow.xaml.vb 文件。  
  
### <a name="building-the-example"></a>生成示例  
 要自行扩展示例，请按“下载示例”部分的说明逐步操作，但要选择“CancelATask”作为“启动项目”。 向该项目添加下列更改。 星号标记了程序中的更改。  
  
1.  添加一个方法，用于创建 Web 地址的列表。  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  在 `AccessTheWebAsync` 中调用方法。  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  在 `AccessTheWebAsync` 中添加下列循环，用于处理列表中的每个 Web 地址。  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  由于 `AccessTheWebAsync` 显示了长度，因此该方法无需返回任何内容。 删除返回语句，并将方法的返回类型更改为 <xref:System.Threading.Tasks.Task>，而不是 <xref:System.Threading.Tasks.Task%601>。  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     使用语句而非表达式从 `startButton_Click` 调用方法。  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  如果不取消该程序，它将生成以下输出。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     如果在下载完成之前选择“取消”按钮，则输出将包含取消前已完成下载的长度。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
## <a name="BKMK_CompleteExamples"></a>完成示例  
 以下各部分包含每个前面示例的代码。 请注意，必须为 <xref:System.Net.Http> 添加引用。  
  
 您可以下载的项目从[异步示例：Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)（异步示例：微调应用程序）下载这些项目。  
  
### <a name="cancel-a-task-example"></a>取消任务示例  
 以下代码是取消单个任务的示例的完整 MainWindow.xaml.vb 文件。  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a>取消任务列表示例  
 以下代码是取消任务列表的示例的完整 MainWindow.xaml.vb 文件。  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [使用 Async 和 Await 的异步编程 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [微调异步应用程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [异步示例：微调应用程序](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
