---
title: 如何：强制自变量传递的值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842039"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>如何：强制自变量传递的值 (Visual Basic)
过程声明确定的传递机制。 如果声明的参数[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 希望按引用传递相应的参数。 这将允许过程来更改调用代码中的参数的基础编程元素的值。 如果你想要防止此类更改基础元素，则可以重写`ByRef`传递机制在过程调用将参数名称括在括号中。 这些括号是除了括号之外的参数列表的调用中。  
  
 调用代码不能重写[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)机制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>若要强制通过值传递自变量  
  
-   如果声明的相应参数`ByVal`在过程中，不需要执行任何其他步骤。 Visual Basic 已预期按值传递参数。  
  
-   如果声明的相应参数`ByRef`在过程中，将括在括号中的过程调用中的参数。  
  
## <a name="example"></a>示例  
 下面的示例替代`ByRef`参数声明。 强制在调用中`ByVal`，请注意两个级别的括号。  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 时`str`都包含在参数列表中的额外圆括号`setNewString`过程不能更改在调用代码中，其值和`MsgBox`显示"不能替换如果传递 ByVal"。 当`str`不包含在额外的括号，该过程可以更改它，和`MsgBox`显示"这是新 inString 参数的值"。  
  
## <a name="compiling-the-code"></a>编译代码  
 当通过引用传递变量时，必须使用`ByRef`关键字来指定此机制。  
  
 Visual Basic 中的默认值是按值传递参数。 但是，它是一个良好的编程做法包括[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)关键字与每个声明的参数。 这使您的代码易于阅读。  
  
## <a name="robust-programming"></a>可靠编程  
 如果一个过程声明了形参[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正确执行代码可能依赖于无法更改调用代码中的基础元素。 如果调用代码重写此调用的机制，通过将实参括在括号内，或者如果它传递不可修改自变量，该过程不能更改基础元素。 这可能会产生意外的结果调用代码中。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允许更改基础调用代码中的自变量的值的过程中始终没有带来潜在的风险。 请确保您希望此值可更改，并且准备好使用它之前检查其有效性。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可修改和不可修改自变量之间的差异](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [通过值传递自变量和通过引用传递自变量之间的差异](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：更改过程自变量的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
