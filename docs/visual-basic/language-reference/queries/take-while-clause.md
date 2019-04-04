---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 080a106fc1deeb54165511ed03d7c7c5d2060f21
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818744"
---
# <a name="take-while-clause-visual-basic"></a>Take While 子句 (Visual Basic)
包括集合中指定条件为 `true` 的任何元素，并绕过剩余元素。  
  
## <a name="syntax"></a>语法  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`expression`|必需。 一个表达式，表示要测试的元素的条件。 该表达式必须返回`Boolean`值或功能上等效，如`Integer`被视为`Boolean`。|  
  
## <a name="remarks"></a>备注  
 `Take While`子句之前提供包括查询结果的开始元素`expression`返回`false`。 之后`expression`返回`false`，查询将跳过所有剩余元素。 `expression`忽略其余的结果。  
  
 `Take While`子句不同于`Where`中的子句`Where`子句可用于包括从查询满足特定条件的所有元素。 `Take While`子句仅在未满足的条件的第一个时间前包括元素。 `Take While`子句正在使用排序的查询结果时最有用。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Take While`子句来检索结果，直到找到第一个客户，而无需任何订单。  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
