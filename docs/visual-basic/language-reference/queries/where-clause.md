---
title: Where 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 5632e69039baebb3d1f1fd90c04586d9e50fe40f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834499"
---
# <a name="where-clause-visual-basic"></a>Where 子句 (Visual Basic)
指定查询的筛选条件。  
  
## <a name="syntax"></a>语法  
  
```  
Where condition  
```  
  
## <a name="parts"></a>部件  
 `condition`  
 必需。 一个表达式，确定输出集合中是否包含在集合中的当前项的值。 该表达式的计算结果必须为`Boolean`的等效项或值`Boolean`值。 如果条件计算结果为`True`，该元素是包含在查询结果; 否则为查询结果中排除该元素。  
  
## <a name="remarks"></a>备注  
 `Where`子句，可以通过选择满足特定条件的元素来筛选查询数据。 元素的值会导致`Where`子句来计算结果为`True`包含在查询结果; 中排除其他元素。 使用中的表达式`Where`子句的计算结果必须为`Boolean`或等效于`Boolean`，如计算结果为一个整数`False`时其值为 0。 可以组合多个表达式以`Where`通过使用逻辑运算符，如子句`And`， `Or`， `AndAlso`， `OrElse`， `Is`，和`IsNot`。  
  
 默认情况下，查询无法计算的表达式直到被访问，例如，当它们进行数据绑定或在进行循环访问时`For`循环。 因此，`Where`访问查询之前不计算子句。 如果您具有值的查询中使用的外部`Where`子句，确保适当的值在中使用`Where`子句在执行查询的时间。 有关执行查询的详细信息，请参阅[编写你的第一个 LINQ 查询](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
 可以调用中的函数`Where`子句执行计算或操作的值从集合中的当前元素。 调用函数`Where`子句可能会导致立即定义后而不是受访问时执行的查询。 有关执行查询的详细信息，请参阅[编写你的第一个 LINQ 查询](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。  
  
## <a name="example"></a>示例  
 下面的查询中使用表达式`From`子句来声明范围变量`cust`每个`Customer`对象中`customers`集合。 `Where`子句使用的范围变量将输出限制为客户，从指定的区域。 `For Each`循环显示查询结果中的每个客户的公司名称。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>示例  
 下面的示例使用`And`并`Or`中的逻辑运算符`Where`子句。  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
