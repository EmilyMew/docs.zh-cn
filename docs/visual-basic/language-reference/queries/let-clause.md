---
title: Let 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828692"
---
# <a name="let-clause-visual-basic"></a>Let 子句 (Visual Basic)
计算一个值，并将其分配给在查询中的新变量。  
  
## <a name="syntax"></a>语法  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`variable`|必需。 别名可用于引用提供的表达式的结果。|  
|`expression`|必需。 一个表达式，将计算并分配给指定的变量。|  
  
## <a name="remarks"></a>备注  
 `Let`子句，可计算每个值的查询结果，可以使用别名来引用它们。 别名可在其他子句，如`Where`子句。 `Let`子句，可创建的查询语句，从而更易于进行读取，因为可以为包含在查询表达式子句指定别名，并将每次使用该表达式子句的别名。  
  
 可以包含任意数量的`variable`并`expression`中的分配`Let`子句。 请用逗号 （，） 分隔每个分配。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Let`子句来计算产品上有 10%的折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
