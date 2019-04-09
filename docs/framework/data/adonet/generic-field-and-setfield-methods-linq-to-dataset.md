---
title: 泛型字段和 SetField 方法 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 7c7f1fef5d1fa575cd6d3bfdb7e6cbbea79ade28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086008"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>泛型字段和 SetField 方法 (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 提供扩展方法<xref:System.Data.DataRow>用于访问列值的类：<xref:System.Data.DataRowExtensions.Field%2A>方法和<xref:System.Data.DataRowExtensions.SetField%2A>方法。 这些方法使开发人员能够更轻松地访问列值，特别是 Null 值。 <xref:System.Data.DataSet> 使用 <xref:System.DBNull.Value> 来表示 Null 值，而 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 使用 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 中引入的可以为 null 的类型支持。 使用 <xref:System.Data.DataRow> 中预先存在的列访问器需要将返回对象强制转换成相应的类型。 如果 <xref:System.Data.DataRow> 中的特定字段可以为 null，则必须显示检查 Null 值，因为返回 <xref:System.DBNull.Value> 并隐式地将其强制转换为另一种类型会引发 <xref:System.InvalidCastException>。 在下面的示例中，如果不使用 <xref:System.Data.DataRow.IsNull%2A> 方法检查 Null 值，则在索引器返回 <xref:System.DBNull.Value> 并试图将其强制转换为 <xref:System.String> 的情况下会引发异常。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法提供对 <xref:System.Data.DataRow> 列值的访问，而 <xref:System.Data.DataRowExtensions.SetField%2A> 设置 <xref:System.Data.DataRow>中的列值。 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都可以处理可以为 null 的类型，因此不必像前面的示例那样检查 Null 值。 这两种方法也都是泛型方法，因此不必强制转换返回类型。  
  
 下面的示例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 请注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法的泛型参数 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的数据类型必须与基础值的类型相匹配。 否则，将引发 <xref:System.InvalidCastException> 异常。 指定的列名称也必须与 <xref:System.Data.DataSet> 中的列名称相匹配，否则将引发 <xref:System.ArgumentException>。 在这两种情况下，异常都是在执行查询期间的运行时数据枚举时引发的。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不执行任何类型转换。 但这并不意味着不会发生类型转换。 <xref:System.Data.DataRowExtensions.SetField%2A> 方法公开 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 类的 <xref:System.Data.DataRow> 行为。 类型转换可以由 <xref:System.Data.DataRow> 对象执行，转换的值随后将保存到 <xref:System.Data.DataRow> 对象。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataRowExtensions>
