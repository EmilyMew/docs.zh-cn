---
title: 对数据进行分组 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: c658ac5c46baec1bfa976074b78ac86d791b6515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842049"
---
# <a name="grouping-data-visual-basic"></a>对数据进行分组 (Visual Basic)
分组是指将数据分到不同的组，使每组中的元素拥有公共的属性。  
  
 下图演示了对字符序列进行分组的结果。 每个组的键是字符。  
  
 ![LINQ 分组操作](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 下一节列出了对数据元素进行分组的标准查询运算符方法。  
  
## <a name="methods"></a>方法  
  
|方法名|描述|Visual Basic 查询表达式语法|详细信息|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|对共享通用属性的元素进行分组。 每组由一个 <xref:System.Linq.IGrouping%602> 对象表示。|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|将元素插入基于键选择器函数的 <xref:System.Linq.Lookup%602>（一种一对多字典）。|不适用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查询表达式语法示例  
 下列代码示例根据奇偶性，使用 `Group By` 子句对列表中的整数进行分组。  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Linq>
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [如何：文件分组依据扩展 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [如何：使用组 (LINQ) (Visual Basic 中) 将一个文件拆分成多个文件](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
