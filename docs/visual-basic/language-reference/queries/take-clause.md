---
title: Take 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816949"
---
# <a name="take-clause-visual-basic"></a>Take 子句 (Visual Basic)
从集合的开头返回指定数量的连续元素。  
  
## <a name="syntax"></a>语法  
  
```  
Take count  
```  
  
## <a name="parts"></a>部件  
 `count`  
 必需。 一个值或表达式的计算结果为要返回的序列的元素数量。  
  
## <a name="remarks"></a>备注  
 `Take`子句会使查询，以便包括指定的数量的结果列表的开始的连续元素。 指定要包括的元素数`count`参数。  
  
 可以使用`Take`子句与`Skip`子句从查询的任何段返回一系列数据。 若要执行此操作，将传递到范围内的第一个元素的索引`Skip`子句和范围的大小`Take`子句。 在这种情况下，`Take`子句必须指定后`Skip`子句。  
  
 当你使用`Take`查询中的子句，您可能还需要确保将启用的顺序返回结果`Take`子句，以包括预期的结果。 对查询结果进行排序的详细信息，请参阅[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 可以使用`TakeWhile`子句来指定只有某些元素返回，具体取决于提供的条件。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Take`子句一起使用`Skip`子句，以从页中的查询返回的数据。 GetCustomers 函数使用`Skip`子句以跳过列表中的客户，直到提供的起始索引值，并使用`Take`子句返回的客户从该索引值开始页。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
