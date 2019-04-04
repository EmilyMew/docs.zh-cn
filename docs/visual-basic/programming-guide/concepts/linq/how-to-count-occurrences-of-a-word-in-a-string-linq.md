---
title: 如何：计数的某个词在字符串 (LINQ) (Visual Basic 中) 中的匹配项
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820316"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>如何：计数的某个词在字符串 (LINQ) (Visual Basic 中) 中的匹配项
此示例演示如何使用 LINQ 查询对指定词在字符串中出现的次数进行计数。 请注意，若要执行计数，首先需调用 <xref:System.String.Split%2A> 方法来创建词数组。 <xref:System.String.Split%2A> 方法存在性能开销。 如果只需要统计字符串的字数，则应考虑改用 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 或 <xref:System.String.IndexOf%2A> 方法。 但是，如果性能不是关键问题，或者已拆分句子以对其执行其他类型的查询，则使用 LINQ 来计数词或短语同样有意义。  
  
## <a name="example"></a>示例  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 创建面向 .NET Framework 3.5 或更高版本的项目，此项目包含对 System.Core.dll 的引用和用于 System.Linq 命名空间的 `Imports` 语句。  
  
## <a name="see-also"></a>请参阅

- [LINQ 和字符串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
