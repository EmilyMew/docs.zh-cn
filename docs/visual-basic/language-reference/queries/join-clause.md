---
title: Join 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 21432b95b30ae38ac2cbc9e55b5a3066f0bef665
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825841"
---
# <a name="join-clause-visual-basic"></a>Join 子句 (Visual Basic)
将两个集合合并为单个集合。 联接运算基于匹配键，并使用`Equals`运算符。  
  
## <a name="syntax"></a>语法  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>部件  
 `element`  
 必需。 要联接的集合控制变量。  
  
 `collection`  
 必需。 要结合上左侧和右侧的标识的集合的集合`Join`运算符。 一个`Join`子句可以嵌套在另一个`Join`子句，或在`Group Join`子句。  
  
 `joinClause`  
 可选。 一个或多个其他`Join`进一步优化查询。  
  
 `groupJoinClause`  
 可选。 一个或多个其他`Group Join`进一步优化查询。  
  
 `key1` `Equals` `key2`  
 必需。 标识要联接的集合的键。 必须使用`Equals`运算符比较要联接的集合中的密钥。 您可以通过使用组合联接条件`And`运算符来标识多个密钥。 `key1` 在左侧和右侧的集合中必须是`Join`运算符。 `key2` 从集合中的右侧必须是`Join`运算符。  
  
 联接条件中使用的密钥可以包含多个集合中的项的表达式。 但是，每个键的表达式可以包含仅从其各自的集合的项。  
  
## <a name="remarks"></a>备注  
 `Join`子句将两个集合根据匹配的键值从要联接的集合。 生成的集合可以包含在左侧和右侧的标识的集合中的值的任意组合`Join`运算符，并在标识的集合`Join`子句。 该查询将返回仅为其通过将指定的条件的结果`Equals`满足运算符。 这相当于`INNER JOIN`SQL 中。  
  
 可以使用多个`Join`中加入两个或多个集合合并为单个集合的查询子句。  
  
 您可以执行隐式联接来组合集合而无需`Join`子句。 若要执行此操作，包括多个`In`中的子句你`From`子句并指定`Where`子句，它标识想要用于联接的密钥。  
  
 可以使用`Group Join`子句来组合为单个分层集合的集合。 这就像`LEFT OUTER JOIN`SQL 中。  
  
## <a name="example"></a>示例  
 下面的代码示例执行隐式联接来组合和其订单的客户列表。  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a>示例  
 下面的代码示例通过使用联接两个集合`Join`子句。  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 此示例将生成类似于以下输出：  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>示例  
 下面的代码示例通过使用联接两个集合`Join`子句与两个键列。  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 此示例将生成类似于以下输出：  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查询](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join 子句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
