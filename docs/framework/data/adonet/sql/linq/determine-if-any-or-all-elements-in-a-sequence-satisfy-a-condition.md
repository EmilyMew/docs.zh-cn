---
title: 确定序列中任何或所有元素是否满足某一条件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128331"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>确定序列中任何或所有元素是否满足某一条件
如果序列中的所有元素都满足某一项条件，则 <xref:System.Linq.Enumerable.All%2A> 运算符会返回 `true`。  
  
 如果序列中的任意一个元素满足某一项条件，则 <xref:System.Linq.Queryable.Any%2A> 运算符会返回 `true`。  
  
## <a name="example"></a>示例  
 下面的示例返回由至少下了一个订单的客户组成的序列。 `Where` / `where`子句的计算结果为`true`如果给定`Customer`具有任何`Order`。  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>示例  
 下面的 Visual Basic 代码确定未下订单的客户的列表，并确保对于该列表中的每一位客户，都提供了联系人名称。  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>示例  
 下面的 C# 示例返回由订单包含以“C”开头的 `ShipCity` 的客户组成的序列。 返回结果中还包括未下订单的客户。 （按照设计，对于空序列，<xref:System.Linq.Queryable.All%2A> 运算符返回 `true`。）通过使用 `Count` 运算符在控制台输出中消除了未下订单的客户。  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>请参阅

- [查询示例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
