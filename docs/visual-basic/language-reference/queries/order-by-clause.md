---
title: Order By 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835006"
---
# <a name="order-by-clause-visual-basic"></a>Order By 子句 (Visual Basic)
指定查询结果的排序顺序。  
  
## <a name="syntax"></a>语法  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>部件  
 `orderExp1`  
 必需。 一个或多个字段从当前的查询结果，确定如何对返回的值进行排序。 必须由逗号 （，） 分隔的字段名称。 您可以标识每个字段，为按升序或降序排序，通过使用`Ascending`或`Descending`关键字。 如果没有`Ascending`或`Descending`指定关键字时，默认的排序顺序为升序。 从左到右的优先顺序提供排序顺序字段。  
  
## <a name="remarks"></a>备注  
 可以使用`Order By`子句的查询结果进行排序。 `Order By`子句只能在排序基于当前作用域的范围变量的结果。 例如，`Select`子句引入一个新作用域在查询表达式中使用新的迭代变量的作用域。 之前定义的范围变量`Select`子句的查询中将不可用之后`Select`子句。 因此，如果你想要通过中不可用的字段对结果进行排序`Select`子句中，必须将放`Order By`之前的子句`Select`子句。 一个需要执行此操作的示例是当你想不作为结果的一部分返回的字段的查询结果进行排序时。  
  
 升序和降序顺序的实现决定字段<xref:System.IComparable>字段的数据类型的接口。 如果数据类型不实现<xref:System.IComparable>接口，排序顺序将被忽略。  
  
## <a name="example"></a>示例  
 下面的查询中使用表达式`From`子句来声明范围变量`book`为`books`集合。 `Order By`子句对查询结果进行排序的价格以升序 （默认值）。 按标题以升序排序书籍，其价格相同。 `Select`子句中选择`Title`和`Price`由查询返回的值的属性。  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>示例  
 下面的查询表达式使用`Order By`子句来按价格以降序对查询结果进行排序。 按标题以升序排序书籍，其价格相同。  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>示例  
 下面的查询表达式使用`Select`选择书名、 价格、 发布日期，并编写的子句。 然后填充`Title`， `Price`， `PublishDate`，和`Author`新作用域的范围变量的字段。 `Order By`子句进行排序的作者姓名、 书籍标题和价格的新范围变量。 每个列是按默认顺序 （升序） 排序。  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
