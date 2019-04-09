---
title: 如何：直接执行 SQL 查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101531"
---
# <a name="how-to-directly-execute-sql-queries"></a>如何：直接执行 SQL 查询
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 将转换成参数化 SQL 查询 （以文本形式） 编写的查询并将其发送到 SQL 服务器进行处理。  
  
 SQL 无法执行可由您的应用程序在本地使用的各种方法。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 尝试将这些本地方法转换为等效操作和 SQL 环境中可用的函数。 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 内置类型中的大多数方法和运算符都能直接转换成 SQL 命令。 有些则可以用可用的函数生成。 无法生成的那些方法和运算符会产生运行时异常。 有关详细信息，请参阅[SQL-CLR 类型映射](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
 如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询不足以满足专门任务的需要，你可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法来执行 SQL 查询，然后将查询的结果直接转换成对象。  
  
## <a name="example"></a>示例  
 在下面的示例中，假定 `Customer` 类的数据分布在两个表（customer1 和 customer2）中。 此查询将返回 `Customer` 对象的序列。  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 只要表格结果中的列名与您的实体类的列属性匹配，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就会为您创建不在任何 SQL 查询范围之内的对象。  
  
## <a name="example"></a>示例  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允许带有参数。 请使用类似如下内容的代码来执行参数化查询。  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 在查询文本中使用 `Console.WriteLine()` 和 `String.Format()` 所用的大括号表示法来表示参数。 事实上，`String.Format()`实际上在您提供，如替换大括号内的参数与生成的参数名的查询字符串上调用@p0， @p1 ...， @p(n)。  
  
## <a name="see-also"></a>请参阅

- [背景信息](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [查询数据库](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
