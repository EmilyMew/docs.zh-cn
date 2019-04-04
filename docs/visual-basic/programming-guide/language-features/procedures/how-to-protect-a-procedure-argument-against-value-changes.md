---
title: 如何：防止过程自变量的值发生更改 (Visual Basic)
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
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 70378b57c6d3af5a98e0ba9c6e3aebc319561b1b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837775"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>如何：防止过程自变量的值发生更改 (Visual Basic)
如果一个过程声明为参数[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 使过程代码中调用代码参数的基础的编程元素直接引用。 这将允许更改调用代码中的实参的值的过程。 在某些情况下调用的代码可能想要防止此类更改。  
  
 你可以始终防止自变量的更改中通过声明的相应参数[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)过程中。 如果你想要将无法更改在某些情况下，而不是其他中给定的参数，可以将其声明`ByRef`并让调用代码确定每个调用中的传递机制。 之所以如此是因为相应的参数中括号括起来，将它传递的值，或不将其括起来在括号中以通过引用进行传递。 有关详细信息，请参阅[如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示两个过程采用一个数组变量并运行它的元素。 `increase`过程只需添加一个到每个元素。 `replace`过程将一个新数组分配给该参数`a()`，然后添加一个到每个元素。 但是，重新分配不影响调用代码中的基础数组变量。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一个`MsgBox`调用显示"increase(n) 后：11, 21, 31, 41". 因为数组`n`是引用类型，`increase`可以更改其中一个成员，即使传递机制是`ByVal`。  
  
 第二个`MsgBox`调用显示"replace(n) 后：11, 21, 31, 41". 因为`n`传递`ByVal`，`replace`不能修改变量`n`通过向它分配一个新数组，调用代码中。 当`replace`创建新的数组实例`k`并将其分配给本地变量`a`，它将失去对引用`n`由调用代码传入。 当其更改的成员`a`，只有本地数组`k`受到影响。 因此，`replace`不会增加数组的值`n`调用代码中。  
  
## <a name="compiling-the-code"></a>编译代码  
 Visual Basic 中的默认值是按值传递参数。 但是，它是一个良好的编程做法包括[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)关键字与每个声明的参数。 这使您的代码易于阅读。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可修改和不可修改自变量之间的差异](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [通过值传递自变量和通过引用传递自变量之间的差异](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：更改过程自变量的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
