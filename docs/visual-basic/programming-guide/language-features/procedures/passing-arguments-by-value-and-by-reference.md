---
title: 通过值和通过引用传递参数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: c23ca51322f57dc13a85c3ea94e0d335dc50ca13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830352"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>通过值和通过引用传递参数 (Visual Basic)
在 Visual Basic 中，您可以传递参数给过程*按值*或*按引用*。 这称为*传递机制*，并确定该过程是否可以修改调用代码中的参数的基础的编程元素。 过程声明确定通过指定每个参数的传递机制[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)关键字。  
  
## <a name="distinctions"></a>区别  
 向过程传递参数，应注意的几点彼此交互的差异：  
  
-   基础的编程元素是否可修改或不可修改  
  
-   参数本身是可修改或不可修改  
  
-   自变量通过值或按引用传递  
  
-   参数数据类型是值类型或引用类型  
  
 有关详细信息，请参阅[差异之间可修改和不可修改自变量](./differences-between-modifiable-and-nonmodifiable-arguments.md)并[差异之间传递参数值和按引用来](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>选择的传递机制  
 应选择仔细的每个自变量的传递机制。  
  
-   **保护**。 在两个传递机制之间进行选择，最重要的条件是要更改的调用变量公开。 传递自变量的优点`ByRef`是该过程可以返回给调用代码通过该参数的值。 传递自变量的优点`ByVal`是它可防止变量正在更改的过程。  
  
-   **性能**。 虽然的传递机制可能会影响代码的性能，不同之处是通常并不显著。 一个例外是值类型传递`ByVal`。 在这种情况下，Visual Basic 将复制整个数据内容的自变量。 因此，较大的值类型，如一个结构，它可以更有效，将其传递`ByRef`。  
  
     对于引用类型，仅对数据的指针是复制 （四个字节在 32 位平台上，在 64 位平台上的 8 个字节）。 因此，可以将类型的参数传递`String`或`Object`通过值而不损害性能。  
  
## <a name="determination-of-the-passing-mechanism"></a>确定的传递机制  
 过程声明指定每个参数的传递机制。 调用代码不能重写`ByVal`机制。  
  
 如果与声明的参数`ByRef`，调用代码可以强制机制来`ByVal`将参数名称括在括号内的调用中。 有关详细信息，请参阅[如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 Visual Basic 中的默认值是按值传递参数。  
  
## <a name="when-to-pass-an-argument-by-value"></a>何时按值传递参数  
  
-   如果基础自变量调用的代码元素是不可修改的元素，声明对应的形参[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 没有代码可以更改不可修改的元素的值。  
  
-   如果基础元素是可修改，但不是希望将无法更改其值的过程，将参数声明`ByVal`。 仅调用代码可以更改按值传递的可修改元素的值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>何时按引用传递参数  
  
-   如果该过程有确实需要更改调用代码中的基础元素，声明对应的形参[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
-   如果正确执行代码取决于更改调用代码中的基础元素的过程，将参数声明`ByRef`。 如果将其传递的值，或者调用代码重写`ByRef`括在括号中，自变量传递机制在过程调用可能会产生意外的结果。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例说明了何时按值传递参数，以及何时将它们按引用传递。 过程`Calculate`同时具有`ByVal`和一个`ByRef`参数。 给定利率`rate`，和的总金额的`debt`，该过程的任务是计算新值的`debt`，它是应用到的原始值的利率的结果`debt`。 因为`debt`是`ByRef`参数，对应于在调用代码中的参数的值中反映新的总`debt`。 参数`rate`是`ByVal`参数因为`Calculate`不应更改其值。  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [如何：更改过程自变量的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
