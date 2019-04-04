---
title: 如何：查找两个列表 (LINQ) (Visual Basic 中) 之间的差集
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 2d87a2bd882adb6eca144288ace72b0e7c464907
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829494"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>如何：查找两个列表 (LINQ) (Visual Basic 中) 之间的差集
此示例演示如何使用 LINQ 对两个字符串列表进行比较，并输出那些位于 names1.txt 中但不在 names2.txt 中的行。  
  
### <a name="to-create-the-data-files"></a>创建数据文件  
  
1.  按照[如何：合并和比较字符串集合 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)。  
  
## <a name="example"></a>示例  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 某些类型的查询在 Visual Basic 中的操作，例如<xref:System.Linq.Enumerable.Except%2A>， <xref:System.Linq.Enumerable.Distinct%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Concat%2A>，仅采用基于方法的语法进行表示。  
  
## <a name="compiling-the-code"></a>编译代码  
 创建面向 .NET Framework 3.5 或更高版本的项目，此项目包含对 System.Core.dll 的引用和用于 System.Linq 命名空间的 `Imports` 语句。  
  
## <a name="see-also"></a>请参阅

- [LINQ 和字符串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
