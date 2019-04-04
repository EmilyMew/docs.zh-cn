---
title: Exit 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832627"
---
# <a name="exit-statement-visual-basic"></a>Exit 语句 (Visual Basic)
退出过程或块，并立即将控制转移到的过程调用或块定义后面的语句。  
  
## <a name="syntax"></a>语法  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>语句  
 `Exit Do`  
 立即退出`Do`循环中将显示。 继续后面的语句执行`Loop`语句。 `Exit Do` 可仅在`Do`循环。 当使用内嵌套`Do`循环，`Exit Do`退出最里面的循环，并将控制转移到下一个较高级别的嵌套。  
  
 `Exit For`  
 立即退出`For`循环中将显示。 继续后面的语句执行`Next`语句。 `Exit For` 可仅在`For`...`Next`或`For Each`...`Next`循环。 当使用内嵌套`For`循环，`Exit For`退出最里面的循环，并将控制转移到下一个较高级别的嵌套。  
  
 `Exit Function`  
 立即退出`Function`它所在的过程。 继续后面的语句调用的语句的执行`Function`过程。 `Exit Function` 可仅在`Function`过程。  
  
 若要指定返回值，可以将值分配给前一行的函数名称`Exit Function`语句。 若要将返回值和退出在一个语句中的函数，则可以使用[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Exit Property`  
 立即退出`Property`它所在的过程。 继续执行调用语句`Property`过程，也就是说，与请求或设置该属性的值的语句。 `Exit Property` 可仅在属性的`Get`或`Set`过程。  
  
 若要指定在返回值`Get`过程中，可以将值分配给前一行的函数名称`Exit Property`语句。 若要将分配的返回值和出口`Get`在一个语句中的过程，则可以使用`Return`语句。  
  
 在中`Set`过程中，`Exit Property`语句等效于`Return`语句。  
  
 `Exit Select`  
 立即退出`Select Case`阻止所在。 继续后面的语句执行`End Select`语句。 `Exit Select` 可仅在`Select Case`语句。  
  
 `Exit Sub`  
 立即退出`Sub`它所在的过程。 继续后面的语句调用的语句的执行`Sub`过程。 `Exit Sub` 可仅在`Sub`过程。  
  
 在中`Sub`过程中，`Exit Sub`语句等效于`Return`语句。  
  
 `Exit Try`  
 立即退出`Try`或`Catch`阻止所在。 继续执行`Finally`阻止如果有的话，或后面的语句与`End Try`否则为语句。 `Exit Try` 可仅在`Try`或`Catch`块中，不能在`Finally`块。  
  
 `Exit While`  
 立即退出`While`循环中将显示。 继续后面的语句执行`End While`语句。 `Exit While` 可仅在`While`循环。 使用时内嵌套`While`循环`Exit While`将控制转移到高循环的一个嵌套级别的循环其中`Exit While`发生。  
  
## <a name="remarks"></a>备注  
 不要混淆`Exit`语句替换`End`语句。 `Exit` 未定义语句的末尾。  
  
## <a name="example"></a>示例  
 以下示例中，在循环条件停止循环时`index`变量是否大于 100。 `If`语句在循环中，但是，导致`Exit Do`语句停止循环索引变量是否大于 10 时。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>示例  
 以下示例将返回值分配为函数名称`myFunction`，然后使用`Exit Function`以从函数返回。  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a>示例  
 下面的示例使用[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)返回值分配并退出该函数。  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>请参阅

- [Continue 语句](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [End 语句](../../../visual-basic/language-reference/statements/end-statement.md)
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)
- [Stop 语句](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Try...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
