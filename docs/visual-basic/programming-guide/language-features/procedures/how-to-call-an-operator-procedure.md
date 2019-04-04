---
title: 如何：调用运算符过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: 46614ad43e7be72c8396f47ba7f5d02185f62827
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837086"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>如何：调用运算符过程 (Visual Basic)
通过在表达式中使用的运算符符号调用运算符过程。 转换运算符，如果您调用[CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)将值从一种数据类型转换为另一个。  
  
 不显式调用运算符过程。 只需使用运算符，或`CType`函数，在赋值语句或表达式，通常使用运算符的相同方式。 Visual Basic 进行到运算符过程调用。  
  
 在类或结构上定义一个运算符也称为*重载*运算符。  
  
### <a name="to-call-an-operator-procedure"></a>若要调用运算符过程  
  
1.  以普通方式在表达式中使用的运算符符号。  
  
2.  请确保操作数的数据类型是相应的运算符和正确的顺序。  
  
3.  运算符按预期方式影响表达式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>若要调用的转换运算符过程  
  
1.  使用`CType`在表达式中。  
  
2.  为确保操作数数据类型进行转换，并按正确的顺序。  
  
3.  `CType` 调用转换运算符过程并返回转换后的值。  
  
## <a name="example"></a>示例  
 下面的示例创建两个<xref:System.TimeSpan>结构，并将它们相加，并将结果存储在第三个<xref:System.TimeSpan>结构。 <xref:System.TimeSpan>结构定义多个标准运算符重载的运算符过程。  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 因为<xref:System.TimeSpan>重载标准`+`运算符，则在计算的值前面的示例调用运算符过程`combinedSpan`。  
  
 调用会话运算符过程的示例，请参阅[如何：使用定义运算符的类](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 请确保类或结构使用定义你想要使用的运算符。  
  
## <a name="see-also"></a>请参阅

- [运算符过程](./operator-procedures.md)
- [如何：定义运算符](./how-to-define-an-operator.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隐式转换和显式转换](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [扩大转换和收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
