---
title: 如何：更改过程自变量 (Visual Basic 中) 的值
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 6aee795fefe36c2ad19390c0ac6d1613b2199415
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837479"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>如何：更改过程自变量 (Visual Basic 中) 的值
在调用过程时，您提供每个自变量对应于一个过程中定义的参数。 在某些情况下，过程代码可以更改基础调用代码中的自变量的值。 在其他情况下，该过程可以更改仅其自变量的本地副本。  
  
 Visual Basic 时调用该过程，创建本地副本的每个参数传递[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 对于每个自变量传递[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 使过程代码中调用代码参数的基础的编程元素直接引用。  
  
 如果调用代码中的基础元素是一个可修改的元素，将参数传递`ByRef`，过程代码可用于直接引用更改调用代码中的元素的值。  
  
## <a name="changing-the-underlying-value"></a>更改基础值  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>若要更改过程自变量调用的代码中的基础值  
  
1.  在过程声明中，指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)对应于参数的参数。  
  
2.  在调用代码中，将作为参数传递的可修改的编程元素。  
  
3.  在调用代码中，不能将放在括号中的参数列表中的参数。  
  
4.  在过程代码中，使用参数名称将值分配给调用代码中的基础元素。  
  
 请参阅示例进一步演示。  
  
## <a name="changing-local-copies"></a>更改本地副本  
 如果调用代码中的基础元素是不可修改的元素，或将参数传递`ByVal`，该过程不能更改调用代码中的其值。 但是，该过程可以更改其这类参数的本地副本。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>若要更改过程自变量的过程代码中的副本  
  
1.  在过程声明中，指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)对应于参数的参数。  
  
     或  
  
     在调用代码中，将括在括号中的参数列表中的参数。 这会强制 Visual Basic，将按值传递自变量，即使相应的参数指定`ByRef`。  
  
2.  在过程代码中，使用参数名称的参数的本地副本分配一个值。 调用代码中的基础值不会更改。  
  
## <a name="example"></a>示例  
 下面的示例演示两个过程采用一个数组变量并运行它的元素。 `increase`过程只需添加一个到每个元素。 `replace`过程将一个新数组分配给该参数`a()`，然后添加一个到每个元素。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一个`MsgBox`调用显示"increase(n) 后：11, 21, 31, 41". 因为数组`n`是引用类型，`replace`可以更改其中一个成员，即使传递机制是`ByVal`。  
  
 第二个`MsgBox`调用显示"replace(n) 后：101, 201, 301". 因为`n`传递`ByRef`，`replace`可以修改变量`n`调用代码和分配给它一个新数组中。 因为`n`是引用类型，`replace`还可以更改其成员。  
  
 可以修改变量本身调用代码中的阻止该过程。 请参阅[如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 当通过引用传递变量时，必须使用`ByRef`关键字来指定此机制。  
  
 Visual Basic 中的默认值是按值传递参数。 但是，它是一个良好的编程做法包括[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)关键字与每个声明的参数。 这使您的代码易于阅读。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允许更改基础调用代码中的自变量的值的过程中始终没有带来潜在的风险。 请确保您希望此值可更改，并且准备好使用它之前检查其有效性。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可修改和不可修改自变量之间的差异](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [通过值传递自变量和通过引用传递自变量之间的差异](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
