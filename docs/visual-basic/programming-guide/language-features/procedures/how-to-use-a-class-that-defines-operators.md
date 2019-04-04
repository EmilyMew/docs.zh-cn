---
title: 如何：使用定义运算符 (Visual Basic) 的类
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829403"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>如何：使用定义运算符 (Visual Basic) 的类
如果使用的类或结构，它定义自己的运算符，则可以在 Visual Basic 中访问这些运算符。  
  
 在类或结构上定义一个运算符也称为*重载*运算符。  
  
## <a name="example"></a>示例  
 以下示例将访问 SQL 结构<xref:System.Data.SqlTypes.SqlString>，用于定义转换运算符 ([CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)) 中的 SQL 字符串和 Visual Basic 字符串之间的两个方向。 使用`CType(` *SQL 字符串表达式*，`String)`若要将 SQL 字符串转换为 Visual Basic 字符串，并`CType(` *Visual Basic 字符串表达式*， <xref:System.Data.SqlTypes.SqlString> `)`将另一个方向。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>结构定义转换运算符 ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) 从`String`到<xref:System.Data.SqlTypes.SqlString>，从另一个<xref:System.Data.SqlTypes.SqlString>到`String`。 将分配的语句`title`到`jobTitle`利用了第一个运算符和<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函数调用使用第二个。  
  
## <a name="compiling-the-code"></a>编译代码  
 请确保类或结构使用定义你想要使用的运算符。 不要假定类或结构具有定义每个运算符可进行重载。 可用运算符列表，请参阅[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
 包括相应`Imports`语句处开始的 SQL 字符串的源文件 (在这种情况下<xref:System.Data.SqlTypes>)。  
  
 你的项目必须具有对 System.Data 和 System.XML 的引用。  
  
## <a name="see-also"></a>请参阅

- [运算符过程](./operator-procedures.md)
- [如何：定义运算符](./how-to-define-an-operator.md)
- [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)
- [如何：调用运算符过程](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [隐式转换和显式转换](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [扩大转换和收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
