---
title: Skip While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839894"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 子句 (Visual Basic)
跳过集合中指定条件为 `true` 的任何元素，然后返回剩余元素。  
  
## <a name="syntax"></a>语法  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`expression`|必需。 一个表达式，表示要测试的元素的条件。 该表达式必须返回`Boolean`值或功能上等效，如`Integer`被视为`Boolean`。|  
  
## <a name="remarks"></a>备注  
 `Skip While`子句跳过从之前所提供的查询结果开头的元素`expression`返回`false`。 之后`expression`返回`false`，该查询返回所有剩余元素。 `expression`忽略其余的结果。  
  
 `Skip While`子句不同于`Where`中的子句`Where`子句可用于排除不满足特定条件的查询，在所有元素。 `Skip While`子句排除仅在未满足的条件的第一个时间前的元素。 `Skip While`子句正在使用排序的查询结果时最有用。  
  
 可以通过使用特定数目的结果从一开始对查询结果的绕过`Skip`子句。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Skip While`子句以跳过的结果，直到找到从美国的第一个客户。  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
