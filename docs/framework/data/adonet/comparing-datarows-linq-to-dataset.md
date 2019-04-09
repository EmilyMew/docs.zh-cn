---
title: 比较 DataRow (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077168"
---
# <a name="comparing-datarows-linq-to-dataset"></a>比较 DataRow (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 定义多种用于比较源元素，以查看它们是否相等的集运算符。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 提供了以下集运算符：  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 这些运算符通过对每个元素集合调用 <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> 和 <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> 方法来比较源元素。 对于 <xref:System.Data.DataRow>，这些运算符执行引用比较，在对表格格式数据执行集合操作的情况下，这通常不是理想的行为。 对于集合运算，通常需要确定元素值而不是元素引用是否相等。 因此，向 <xref:System.Data.DataRowComparer> 中添加了 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 类。 此类可用于比较行值。  
  
 <xref:System.Data.DataRowComparer> 类包含 <xref:System.Data.DataRow> 的值比较实现，所以此类可用于设置集合操作，例如 <xref:System.Linq.Enumerable.Distinct%2A>。 此类不能直接实例化，而必须使用 <xref:System.Data.DataRowComparer.Default%2A> 属性返回 <xref:System.Data.DataRowComparer%601> 的实例。 然后调用 <xref:System.Data.DataRowComparer%601.Equals%2A> 方法并作为输入参数传入要进行比较的两个 <xref:System.Data.DataRow> 对象。 如果两个 <xref:System.Data.DataRowComparer%601.Equals%2A> 对象中排序的列值集合相等，则 `true` 方法返回 <xref:System.Data.DataRow>，否则返回 `false`。  
  
## <a name="example"></a>示例  
 此示例使用 `Intersect` 返回两个表中都存在的联系人。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>示例  
 下面的示例比较两个行并获取它们的哈希代码。  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataRowComparer>
- [将数据加载到数据集中](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [LINQ to DataSet 示例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
