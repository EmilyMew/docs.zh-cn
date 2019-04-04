---
title: 标准查询运算符按执行 (Visual Basic) 方式的分类
ms.date: 07/20/2015
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
ms.openlocfilehash: 6331ad0994e121d2d7007c9999f3a684b83efe6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823210"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>标准查询运算符按执行 (Visual Basic) 方式的分类
标准查询运算符方法的 LINQ to Objects 实现主要通过两种方法之一执行：立即执行和延迟执行。 使用延迟执行的查询运算符可以进一步分为两种类别：流式处理和非流式处理。 如果你了解不同查询运算符的执行方式，则有助于理解从给定查询中获得的结果。 如果数据源是不断变化的，或者如果你要在另一个查询的基础上构建查询，这种帮助尤其明显。 本主题根据标准查询运算符的执行方式对其进行分类。  
  
## <a name="manners-of-execution"></a>执行方式  
  
### <a name="immediate"></a>即时  
 立即执行指的是在代码中声明查询的位置读取数据源并执行运算。 返回单个不可枚举的结果的所有标准查询运算符都立即执行。  
  
### <a name="deferred"></a>推迟  
 延迟执行指的是不在代码中声明查询的位置执行运算。 仅当对查询变量进行枚举时才执行运算，例如通过使用 `For Each` 语句执行。 这意味着，查询的执行结果取决于执行查询而非定义查询时的数据源内容。 如果多次枚举查询变量，则每次结果可能都不同。 几乎所有返回类型为 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IOrderedEnumerable%601> 的标准查询运算符皆以延迟方式执行。  
  
 使用延迟执行的查询运算符可以另外分类为流式处理和非流式处理。  
  
#### <a name="streaming"></a>流式处理  
 流式处理运算符不需要在生成元素前读取所有源数据。 在执行时，流式处理运算符一边读取每个源元素，一边对该源元素执行运算，并在可行时生成元素。 流式处理运算符将持续读取源元素直到可以生成结果元素。 这意味着可能要读取多个源元素才能生成一个结果元素。  
  
#### <a name="non-streaming"></a>非流式处理  
 非流式处理运算符必须先读取所有源数据，然后才能生成结果元素。 排序或分组等运算均属于此类别。 在执行时，非流式处理查询运算符将读取所有源数据，将其放入数据结构，执行运算，然后生成结果元素。  
  
## <a name="classification-table"></a>分类表  
 下表按照执行方法对每个标准查询运算符方法进行了分类。  
  
> [!NOTE]
>  如果某个运算符被标入两个列中，则表示在运算中涉及两个输入序列，每个序列的计算方式不同。 在此类情况下，参数列表中的第一个序列始终以延迟流式处理方式来执行计算。  
  
|标准查询运算符|返回类型|立即执行|延迟的流式处理执行|延迟非流式处理执行|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|单个数值|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|单个数值、TSource 或 TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|单个数值、TSource 或 TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|单个数值|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|TSource 数组|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>请参阅

- <xref:System.Linq.Enumerable>
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [标准查询运算符 (Visual Basic 中) 的查询表达式语法](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
