---
title: Continue 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835371"
---
# <a name="continue-statement-visual-basic"></a>Continue 语句 (Visual Basic)
传输控制立即传递给循环的下一个迭代。  
  
## <a name="syntax"></a>语法  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>备注  
 您可以从内部`Do`， `For`，或`While`到该循环的下一个迭代循环。 控制将传递给循环条件测试，相当于将转移到立即`For`或`While`语句，或设置为`Do`或`Loop`包含的语句`Until`或`While`子句。  
  
 可以使用`Continue`循环，以便传输中的任何位置。 允许控制传输的规则将与具有相同[GoTo 语句](../../../visual-basic/language-reference/statements/goto-statement.md)。  
  
 例如，如果循环是指完全包含在`Try`块中，`Catch`块中，或`Finally`块中，可以使用`Continue`将跳出循环。 如果在另一只手， `Try`...`End Try`结构是否包含在循环内，则不能使用`Continue`若要将控制转移出`Finally`块中，您可以使用它来转移出`Try`或`Catch`阻止仅在完全传输共时`Try`...`End Try`结构。  
  
 如果您具有嵌套的循环的相同的类型，例如`Do`在另一个循环`Do`循环中，`Continue Do`语句将跳到下一个迭代的最内层`Do`包含它的循环。 不能使用`Continue`跳到相同类型的包含循环的下一个迭代。  
  
 如果您有嵌套的循环的不同类型，例如`Do`内循环`For`循环中，则可以跳到任一循环的下一迭代使用`Continue Do`或`Continue For`。  
  
## <a name="example"></a>示例  
 下面的代码示例使用`Continue While`语句可以跳到下一列的数组，如果除数为零。 `Continue While`位于`For`循环。 将对传输`While col < lastcol`语句，这是最内层的下一个迭代`While`循环包含`For`循环。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>请参阅

- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
