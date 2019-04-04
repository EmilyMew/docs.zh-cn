---
title: From 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: b18ef2f291e20d8a150972a980ba063377b0bc3a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839608"
---
# <a name="from-clause-visual-basic"></a>From 子句 (Visual Basic)
指定一个或多个范围变量和查询的集合。  
  
## <a name="syntax"></a>语法  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`element`|必需。 一个*范围变量*用于循环访问集合的元素。 范围变量用于引用的每个成员`collection`根据循环访问查询`collection`。 必须是可枚举类型。|  
|`type`|可选。 `element` 的类型。 如果没有`type`指定的类型`element`从推断`collection`。|  
|`collection`|必需。 表示要查询的集合。 必须是可枚举类型。|  
  
## <a name="remarks"></a>备注  
 `From`子句用于标识源数据中的查询以及用于在源集合中引用的元素的变量。 这些变量称为*范围变量*。 `From`子句是必需的查询，除非当`Aggregate`子句用于确定某个查询仅返回聚合结果。 有关详细信息，请参阅[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 可以指定多个`From`查询来标识要联接的多个集合中的子句。 如果指定多个集合，独立，循环，或如果它们彼此联接它们。 您可以通过使用隐式联接集合`Select`子句，或通过使用显式`Join`或`Group Join`子句。 作为替代方法，您可以指定多个范围变量和集合中单个`From`子句中，每个相关的范围变量和由逗号分隔开的集合。 下面的代码示例显示了有关这两个语法选项`From`子句。  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`子句定义的查询，这是类似的作用域范围`For`循环。 因此，每个`element`查询的作用域中的范围变量必须具有唯一的名称。 因为你可以指定多个`From`子句的查询，后续`From`子句可以引用中的范围变量`From`子句，或它们在早期的范围变量可以引用`From`子句。 例如，下面的示例演示嵌套`From`子句中的第二个子句的集合基于第一个子句中的范围变量的属性。  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 每个`From`子句可以后跟其他查询子句以优化查询的任意组合。 可以按以下方式来优化查询：  
  
-   通过使用隐式组合多个集合`From`并`Select`子句，或通过使用显式`Join`或`Group Join`子句。  
  
-   使用`Where`子句来筛选查询结果。  
  
-   对结果进行排序通过使用`Order By`子句。  
  
-   通过将类似的结果组合在一起`Group By`子句。  
  
-   使用`Aggregate`子句，以标识要针对整个查询结果计算的聚合函数。  
  
-   使用`Let`子句引入迭代变量的值由而不是集合的表达式。  
  
-   使用`Distinct`子句忽略重复的查询结果。  
  
-   标识要通过使用返回的结果的部分`Skip`， `Take`， `Skip While`，和`Take While`子句。  
  
## <a name="example"></a>示例  
 下面的查询中使用表达式`From`子句来声明范围变量`cust`每个`Customer`对象中`customers`集合。 `Where`子句使用的范围变量将输出限制为客户，从指定的区域。 `For Each`循环显示查询结果中的每个客户的公司名称。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>请参阅

- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct 子句](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let 子句](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
