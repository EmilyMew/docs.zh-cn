---
title: 转换数据类型 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: ad9594cabe0e2382ae4e19f2541eec4aa74ccd75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837047"
---
# <a name="converting-data-types-visual-basic"></a>转换数据类型 (Visual Basic)
转换方法可更改输入对象的类型。  
  
 LINQ 查询中的转换运算可用于各种应用程序。 以下是一些示例：  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可用于隐藏类型的标准查询运算符自定义实现。  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可用于为 LINQ 查询启用非参数化集合。  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可用于强制执行即时的查询，而不是将其推迟到枚举该查询时。  
  
## <a name="methods"></a>方法  
 下表列出了执行数据类型转换的标准查询运算符方法。  
  
 本表中名称以“As”开头的转换方法可更改源集合的静态类型，但不对其进行枚举。 名称以“To”开头的方法可枚举源集合，并将项放入相应的集合类型。  
  
|方法名|描述|Visual Basic 查询表达式语法|详细信息|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|返回类型化为 <xref:System.Collections.Generic.IEnumerable%601> 的输入。|不适用。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|将（泛型）<xref:System.Collections.IEnumerable> 转换为（泛型）<xref:System.Linq.IQueryable>。|不适用。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|将集合中的元素转换为指定类型。|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|根据其转换为指定类型的能力筛选值。|不适用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|将集合转换为数组。 此方法强制执行查询。|不适用。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|根据键选择器函数将元素放入 <xref:System.Collections.Generic.Dictionary%602>。 此方法强制执行查询。|不适用。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|将集合转换为 <xref:System.Collections.Generic.List%601>。 此方法强制执行查询。|不适用。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|根据键选择器函数将元素放入 <xref:System.Linq.Lookup%602>（一对多字典）。 此方法强制执行查询。|不适用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查询表达式语法示例  
 下面的代码示例使用`From As`子句将类型转换为子类型访问仅在相应的子类型可用的成员之前。  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Linq>
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)
- [如何：使用 LINQ (Visual Basic) 查询 ArrayList](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
