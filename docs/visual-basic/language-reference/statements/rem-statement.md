---
title: REM 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817014"
---
# <a name="rem-statement-visual-basic"></a>REM 语句 (Visual Basic)
使用要包含在程序的源代码中的说明性备注。  
  
## <a name="syntax"></a>语法  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>部件  
 `comment`  
 可选。 想要包括的任何注释的文本。 是之间需要空格`REM`关键字和`comment`。  
  
## <a name="remarks"></a>备注  
 可以将`REM`上某一行，或在单独的语句可以将其放在另一个语句后的行。 `REM`语句必须是在行上的最后一个语句。 如果它跟在另一个语句，`REM`必须从该语句由空格分隔。  
  
 可以使用单引号 (`'`) 而不是`REM`。 您的评论另一个语句后面的同一行上还是位于单独一行上，也是如此。  
  
> [!NOTE]
>  无法继续`REM`语句通过使用行继续符序列 (`_`)。 注释开始后，编译器不检查具有特殊含义的字符。 对于多行注释，使用另一个`REM`语句或注释符号 (`'`) 在每一行上。  
  
## <a name="example"></a>示例  
 下面的示例演示`REM`用于解释性备注包含在程序中的语句。 它还演示了替代方法，即使用单引号字符 (`'`) 而不是`REM`。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [代码中的注释](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [如何：在代码中拆分和合并语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
