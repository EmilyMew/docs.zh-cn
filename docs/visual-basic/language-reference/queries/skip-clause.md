---
title: Skip 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: db2d79596895505ddaa7778e831082a94c7ad44e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821096"
---
# <a name="skip-clause-visual-basic"></a>Skip 子句 (Visual Basic)
绕过集合中指定数量的元素，然后返回剩余的元素。  
  
## <a name="syntax"></a>语法  
  
```  
Skip count  
```  
  
## <a name="parts"></a>部件  
 `count`  
 必需。 一个值或表达式的计算结果为要跳过序列中的元素数。  
  
## <a name="remarks"></a>备注  
 `Skip`子句会使查询以绕过在结果列表的开始处的元素并返回剩余元素。 要跳过的元素数由`count`参数。  
  
 可以使用`Skip`子句与`Take`子句从查询的任何段返回一系列数据。 若要执行此操作，将传递到范围内的第一个元素的索引`Skip`子句和范围的大小`Take`子句。  
  
 当你使用`Skip`查询中的子句，您可能还需要确保将启用的顺序返回结果`Skip`子句，以绕过预期的结果。 对查询结果进行排序的详细信息，请参阅[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 可以使用`SkipWhile`子句来指定只有某些元素将忽略，具体取决于提供的条件。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Skip`子句一起使用`Take`子句，以从页中的查询返回的数据。 `GetCustomers`函数使用`Skip`子句，以跳过列表中的客户，直到提供的起始索引值，并使用`Take`子句返回的客户从该索引值开始页。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
