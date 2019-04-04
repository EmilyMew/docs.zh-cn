---
title: GoTo 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827765"
---
# <a name="goto-statement"></a>GoTo 语句
无条件地分支到过程中指定的行。  
  
## <a name="syntax"></a>语法  
  
```  
GoTo line  
```  
  
## <a name="part"></a>部件  
 `line`  
 必需。 所有行标签。  
  
## <a name="remarks"></a>备注  
 `GoTo`语句只能跳转到它在其中出现的过程中的行。 在行必须具有的行标签`GoTo`可以引用。 有关详细信息，请参阅[如何：标记语句](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
>  `GoTo` 语句可以使代码难以阅读和维护。 只要有可能，请改为使用控制结构。 有关详细信息，请参阅[控制流](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。  
  
 不能使用`GoTo`语句从外部`For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`，或`Using`...`End Using`构造中为标签。  
  
## <a name="branching-and-try-constructions"></a>分支和尝试构造  
 在`Try`...`Catch`...`Finally`构造中，以下规则适用于与分支`GoTo`语句。  
  
|块或区域|从外部中分支|从内向外分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` 块|只能从`Catch`相同的构造块<sup>1</sup>|只能与整个构造外部|  
|`Catch` 块|永远不允许|只能与整个构造外部或设置为`Try`相同的构造块<sup>1</sup>|  
|`Finally` 块|永远不允许|永远不允许|  
  
 <sup>1</sup>如果一个`Try`...`Catch`...`Finally`构造嵌套在另一个，`Catch`块可以分支到`Try`块在其自己的嵌套级别，但不是到任何其他`Try`块。 嵌套`Try`...`Catch`...`Finally`构造必须完全在包含`Try`或`Catch`块在其中嵌套的构造。  
  
 下图显示了一个`Try`构造嵌套在另一个。 在这两个构造块之间的各分支将予以有效或无效。  
  
 ![Try 结构分支示意图](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>示例  
 下面的示例使用`GoTo`分支到过程中的线条标签的语句。  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>请参阅

- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With 语句](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
