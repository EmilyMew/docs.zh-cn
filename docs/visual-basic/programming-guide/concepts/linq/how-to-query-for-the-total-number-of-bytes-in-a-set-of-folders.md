---
title: 如何：查询的一组文件夹 (LINQ) (Visual Basic 中) 中的字节总数
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 9aa098ddca2e3ad300913b207c9db5a4976eded7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831665"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>如何：查询的一组文件夹 (LINQ) (Visual Basic 中) 中的字节总数
此示例演示如何检索由指定文件夹及其所有子文件夹中的所有文件使用的字节总数。  
  
## <a name="example"></a>示例  
 <xref:System.Linq.Enumerable.Sum%2A> 方法可将 `select` 子句中选择的所有项的值相加。 可轻松修改此查询以检索指定目录树中的最大或最小文件，方法是调用 <xref:System.Linq.Enumerable.Min%2A> 或 <xref:System.Linq.Enumerable.Max%2A> 方法，而不是 <xref:System.Linq.Enumerable.Sum%2A> 方法。  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 如果只需对指定目录树中的字节数进行计数，则可以更高效地执行此操作而无需创建 LINQ 查询（这会产生创建列表集合作为数据源的开销）。 随着查询变得更加复杂，或者在必须对相同数据源运行多个查询时，LINQ 方法会更加有用。  
  
 查询调用单独的方法来获取文件长度。 这是为了使用在以下情况下会引发的可能异常：在 `GetFiles` 调用中创建了 <xref:System.IO.FileInfo> 对象之后，在其他线程中删除了文件。 即使已创建 <xref:System.IO.FileInfo> 对象，该异常也可能出现，因为 <xref:System.IO.FileInfo> 对象会在首次访问其 <xref:System.IO.FileInfo.Length%2A> 属性时，尝试使用最近长度刷新该属性。 通过将此操作置于查询外部的 try-catch 块中，代码可遵循在查询中避免可能导致副作用的操作这一规则。 一般情况下，在使用异常时必须格外谨慎，以确保应用程序不会处于未知状态。  
  
## <a name="compiling-the-code"></a>编译代码  
 创建面向.NET Framework 版本 3.5 或更高版本包含对 System.Core.dll 的引用的项目和一个`Imports`System.Linq 命名空间的语句。  
  
## <a name="see-also"></a>请参阅

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ 和文件目录 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
