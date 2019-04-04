---
title: 运算符过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: e6e65b1a75d7a80caff3e7cbacdb9dd706e46cdf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815565"
---
# <a name="operator-procedures-visual-basic"></a>运算符过程 (Visual Basic)
运算符过程是一系列定义标准运算符的行为的 Visual Basic 语句 (如`*`， `<>`，或`And`) 上的类或结构定义。 这也称为*运算符重载*。  
  
## <a name="when-to-define-operator-procedures"></a>何时定义运算符过程  
 当已定义的类或结构时，可声明为类或结构的类型的变量。 有时此类变量需要参与一个操作作为表达式的一部分。 若要执行此操作，它必须是运算符的操作数。  
  
 Visual Basic 仅在其基本数据类型上定义运算符。 您可以定义一个运算符的行为或两个操作数均为类或结构的类型。  
  
 有关详细信息，请参阅[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="types-of-operator-procedure"></a>类型的运算符过程  
 运算符过程可以是以下类型之一：  
  
-   其中的参数是类或结构的类型的一元运算符的定义。  
  
-   其中至少一个参数是类或结构的类型的二进制运算符的定义。  
  
-   其中的参数是类或结构的类型的转换运算符的定义。  
  
-   转换运算符返回的类或结构类型的定义。  
  
 转换运算符始终是一元，并始终使用`CType`用作您定义的运算符。  
  
## <a name="declaration-syntax"></a>声明语法  
 声明运算符过程的语法如下所示：  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 您使用`Widening`或`Narrowing`关键字仅在类型转换运算符。 运算符符号始终是[CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)的类型转换运算符。  
  
 声明两个操作数定义二元运算符，并声明一个要定义一元运算符，包括类型转换运算符的操作数。 必须声明所有操作数`ByVal`。  
  
 相同的方式声明的参数声明每个操作数[Sub 过程](./sub-procedures.md)。  
  
### <a name="data-type"></a>数据类型  
 要在类或已定义的结构上定义运算符，因为至少一个操作数必须是类或结构的数据类型。 有关类型转换运算符，操作数或返回类型必须是类或结构的数据类型。  
  
 有关更多详细信息，请参阅[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="calling-syntax"></a>调用语法  
 通过在表达式中使用的运算符符号的隐式调用运算符过程。 提供操作数的相同方式为预定义的运算符。  
  
 隐式调用运算符过程的语法如下所示：  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>声明和调用的插图  
 以下结构将 128 位带符号的整数值存储为构成的高序位，低位部分。 它定义`+`运算符将两个`veryLong`值，并生成生成`veryLong`值。  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 下面的示例演示对典型调用`+`上定义的运算符`veryLong`。  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  
  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Sub 过程](./sub-procedures.md)
- [Function 过程](./function-procedures.md)
- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定义运算符](./how-to-define-an-operator.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [如何：调用运算符过程](./how-to-call-an-operator-procedure.md)
- [如何：使用定义运算符的类](./how-to-use-a-class-that-defines-operators.md)
