---
title: Return 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 7f8ec0456576133d37dd19b5c0f8878a7ac57dab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831718"
---
# <a name="return-statement-visual-basic"></a>Return 语句 (Visual Basic)
将控制返回给调用的代码`Function`， `Sub`， `Get`， `Set`，或`Operator`过程。  
  
## <a name="syntax"></a>语法  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>部件  
 `expression`  
 在所需`Function`， `Get`，或`Operator`过程。 表示要返回到调用代码的值的表达式。  
  
## <a name="remarks"></a>备注  
 在中`Sub`或`Set`过程中，`Return`语句是等效于`Exit Sub`或`Exit Property`语句中，和`expression`不得提供。  
  
 在中`Function`， `Get`，或`Operator`过程中，`Return`语句必须包括`expression`，和`expression`的计算结果必须为数据类型转换为该过程的返回类型。 在中`Function`或`Get`过程中，您还可以选择将表达式分配给要用作返回值的过程名称，然后执行`Exit Function`或`Exit Property`语句。 在中`Operator`过程中，必须使用`Return expression`。  
  
 可以包括任意多个`Return`根据需要在同一过程中的语句。  
  
> [!NOTE]
>  中的代码`Finally`块运行`Return`中的语句`Try`或`Catch`块是遇到，但在之前的`Return`语句执行。 一个`Return`语句不能包括在`Finally`块。  
  
## <a name="example"></a>示例  
 下面的示例使用`Return`语句数次以返回到调用代码时该过程无需执行任何其他操作。  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>请参阅

- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get 语句](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
