---
title: Group Join 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821942"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 子句 (Visual Basic)
将两个集合合并为单个分层集合。 联接运算基于匹配键。  
  
## <a name="syntax"></a>语法  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`element`|必需。 要联接的集合控制变量。|  
|`type`|可选。 `element` 的类型。 如果没有`type`指定的类型`element`从推断`collection`。|  
|`collection`|必需。 要与位于左侧和右侧的集合合并的集合`Group Join`运算符。 一个`Group Join`子句可以嵌套在`Join`子句或另一个`Group Join`子句。|  
|`key1` `Equals` `key2`|必需。 标识要联接的集合的键。 必须使用`Equals`运算符比较要联接的集合中的密钥。 您可以通过使用组合联接条件`And`运算符来标识多个密钥。 `key1`参数必须是从左侧集合`Join`运算符。 `key2`参数必须是从右侧集合`Join`运算符。<br /><br /> 联接条件中使用的密钥可以包含多个集合中的项的表达式。 但是，每个键的表达式可以包含仅从其各自的集合的项。|  
|`expressionList`|必需。 标识如何聚合的组集合中元素的一个或多个表达式。 若要标识分组结果的成员名称，请使用`Group`关键字 (`<alias> = Group`)。 还可以包含聚合函数以将其应用于该组。|  
  
## <a name="remarks"></a>备注  
 `Group Join`子句将两个集合根据匹配的键值从要联接的集合。 生成的集合可以包含引用的元素的集合中第一个集合中的键值匹配的第二个集合的成员。 此外可以指定要应用于分组元素从第二个集合的聚合函数。 有关聚合函数的信息，请参阅[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 例如，考虑，经理的集合和员工的集合。 从这两个集合的元素具有 ManagerID 属性，用于标识向特定经理的员工。 联接运算的结果将包含每个管理器和员工具有匹配 ManagerID 值的结果。 从结果`Group Join`操作将包含管理器的完整列表。 每个管理器结果都将包含所引用的是特定的管理器的匹配项的员工列表的成员。  
  
 产生的集合`Group Join`操作可以包含从集合中标识的值的任意组合`From`子句和表达式中标识`Into`子句`Group Join`子句。 有关有效表达式的详细信息`Into`子句，请参阅[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。  
  
 一个`Group Join`操作将从上左侧和右侧的标识集合中返回所有结果`Group Join`运算符。 即使被联接集合中没有匹配项，这是如此。 这就像`LEFT OUTER JOIN`SQL 中。  
  
 可以使用`Join`子句来组合成单个集合的集合。 这相当于`INNER JOIN`SQL 中。  
  
## <a name="example"></a>示例  
 下面的代码示例通过使用联接两个集合`Group Join`子句。  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join 子句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 子句](../../../visual-basic/language-reference/queries/group-by-clause.md)
