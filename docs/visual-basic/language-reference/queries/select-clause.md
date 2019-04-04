---
title: Select 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 367d810c2358963bfe2f092a390443eccdc66941
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814440"
---
# <a name="select-clause-visual-basic"></a>Select 子句 (Visual Basic)
定义查询的结果。  
  
## <a name="syntax"></a>语法  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>部件  
 `var1`  
 可选。 一个可用于引用的列表达式结果的别名。  
  
 `fieldName1`  
 必需。 要返回查询结果中的字段的名称。  
  
## <a name="remarks"></a>备注  
 可以使用`Select`子句定义要从查询返回的结果。 这使你可以定义的查询，创建的新匿名类型成员或目标的查询返回的命名类型的成员。 `Select`子句不是必需的查询。 如果没有`Select`指定子句，则查询将返回基于为当前作用域标识的范围变量的所有成员的类型。 有关详细信息，请参阅[匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。 当查询创建一个已命名的类型时，它将返回类型的结果<xref:System.Collections.Generic.IEnumerable%601>其中`T`是创建的类型。  
  
 `Select`子句可以引用当前作用域中的任何变量。 这包括中标识的范围变量`From`子句 (或`From`子句)。 它还包括使用的别名创建任何新变量`Aggregate`， `Let`， `Group By`，或`Group Join`子句或从以前的变量`Select`查询表达式中的子句。 `Select`子句还可以包含静态值。 例如，下面的代码示例演示查询表达式所在`Select`子句将查询结果定义为具有四个成员的新匿名类型： `ProductName`， `Price`， `Discount`，和`DiscountedPrice`。 `ProductName`并`Price`成员值取自中定义的产品范围变量`From`子句。 `DiscountedPrice`中计算成员值`Let`子句。 `Discount`成员是静态值。  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`子句引入了一组新的后续查询子句的范围变量和之前的范围变量将不再在作用域中。 最后一个`Select`查询表达式中的子句将确定查询的返回值。 例如，以下查询将返回公司名称和订单总计超过 500 的每个客户订单 ID。 第一个`Select`子句标识的范围变量`Where`子句和第二个`Select`子句。 第二个`Select`子句标识作为新的匿名类型的查询返回的值。  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 如果`Select`子句标识要返回的单个项，在查询表达式返回的单个项的类型的集合。 如果`Select`子句标识要返回的多个项，在查询表达式返回基于所选的项的新匿名类型的集合。 例如，以下两个查询返回基于两个不同类型的集合`Select`子句。 第一个查询返回以字符串形式的公司名称的集合。 第二个查询返回的集合`Customer`使用公司名称和地址信息填充的对象。  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>示例  
 下面的查询中使用表达式`From`子句来声明范围变量`cust`为`customers`集合。 `Select`子句中选择客户名称和 ID 值并填充`CompanyName`和`CustomerID`的新范围变量的列。 `For Each`语句循环访问每个返回的对象，并显示`CompanyName`和`CustomerID`为每个记录的列。  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
