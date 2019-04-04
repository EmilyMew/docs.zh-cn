---
title: Function 过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 568489d6034316e895cd999801241fa995aadefa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834239"
---
# <a name="function-procedures-visual-basic"></a>Function 过程 (Visual Basic)
一个`Function`过程是 Visual Basic 语句括在一系列`Function`和`End Function`语句。 `Function`过程执行一项任务，再将控制权返回到调用代码。 当它返回控制时，它还向调用代码返回一个值。  
  
 每次调用该过程时，运行时，其语句开头的第一个可执行语句后`Function`语句，并与第一个结束`End Function`， `Exit Function`，或`Return`遇到语句。  
  
 您可以定义`Function`模块、 类或结构中的过程。 它是`Public`默认情况下，这意味着可以从任何位置调用在有权访问模块、 类或结构定义它的应用程序中。  
  
 一个`Function`过程可以采用自变量，如常量、 变量或表达式，通过调用代码传递给它。  
  
## <a name="declaration-syntax"></a>声明语法  
 声明的语法`Function`过程如下所示：  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *修饰符*可以指定访问级别和重载、 重写、 共享和隐藏有关的信息。 有关详细信息，请参阅[Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 将每个参数声明为执行操作的相同方式[Sub 过程](./sub-procedures.md)。  
  
### <a name="data-type"></a>数据类型  
 每个`Function`过程具有数据类型，只需为每个变量执行。 通过指定此数据类型`As`子句中的`Function`语句，并且它确定该函数将返回到调用代码的值的数据类型。 下面的示例声明说明这一点。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 详细信息，请参阅"部分"中[Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="returning-values"></a>返回值  
 值`Function`过程将发送回调用代码名为其返回值。 此过程返回此值在两种方式之一：  
  
-   它使用`Return`语句以指定返回值，并返回到调用程序立即控制。 下面的示例阐释了这一点。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   它将值分配给自己的过程的一个或多个语句中的函数名称。 控件不返回给调用程序直到`Exit Function`或`End Function`执行语句。 下面的示例阐释了这一点。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 将返回值分配给函数名称的优点是，控件才会返回的过程中遇到`Exit Function`或`End Function`语句。 这样，您可以分配的初步值和更高版本调整，如有必要。  
  
 有关返回值的详细信息，请参阅[Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)。 返回数组的信息，请参阅[数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="calling-syntax"></a>调用语法  
 调用`Function`过程的方法是将其名称和参数放在赋值语句或表达式中的右侧。 您必须是不可选的所有自变量提供值，必须将参数列表括在括号中。 如果未不提供任何参数，可以选择性地省略括号。  
  
 对的调用语法`Function`过程如下所示：  
  
 *lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`  
  
 当您调用`Function`过程中，您无需使用它的返回值。 如果不这样做，将执行的函数的所有操作，而将忽略返回值。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 以这种方式通常称为。  
  
### <a name="illustration-of-declaration-and-call"></a>声明和调用的插图  
 以下`Function`过程计算的最长边或斜边的直角三角形而言，其他两个方面为给定的值。  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 下面的示例演示对典型调用`hypotenuse`。  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [属性过程](./property-procedures.md)
- [运算符过程](./operator-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：创建一个过程，返回一个值](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：从过程返回值](./how-to-return-a-value-from-a-procedure.md)
- [如何：调用返回的值的过程](./how-to-call-a-procedure-that-returns-a-value.md)
