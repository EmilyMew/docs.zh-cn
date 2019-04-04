---
title: 将“ByRef”参数“<parametername>”的值复制回匹配的参数将导致从类型“<typename1>”到类型“<typename2>”的收缩转换
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: fa8607bf72dfb344048ec82514182dcb6810274d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817149"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>复制的 ByRef 参数值\<parametername > 返回到匹配的参数用于限制从类型\<typename1 > 类型\<typename2 >
加宽到相应的参数类型，由自变量调用过程时，从参数的参数转换为收缩转换。  
  
 在定义类或结构时，可以定义一个或多个转换运算符来将该类或结构类型转换为其他类型。 也可以定义反向转换运算符来将这些其他类型转换回类或结构类型。 当在过程调用中使用你的类或结构类型时，Visual Basic 可以使用这些转换运算符来将自变量的类型转换为其对应的参数类型。  
  
 如果传递参数[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 有时会将参数值复制到本地变量中而不是传递一个引用，该过程。 在这种情况下，当过程返回时，Visual Basic 必须然后将本地变量值复制回调用代码中的参数。  
  
 如果将 `ByRef` 实参值复制到过程中，并且实参与形参为同一类型，则不必进行转换。 但如果类型不同，必须将 Visual Basic 转换两个方向。 如果你的类或结构类型的类型之一，Visual Basic 必须将其转换到和从其他类型。 如果其中一个这些转换扩大转换，则可能会收缩反向转换。  
  
 **错误 ID:** BC32053  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果可能，请与过程参数，使用相同类型的调用参数，因此 Visual Basic 不需要执行任何转换。  
  
-   如果需要调用实参类型与形参类型不同的过程，但不需要将值返回到调用实参中，请将形参定义为 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) 而不是 `ByRef`。  
  
-   如果你需要将值返回到调用的参数，定义反向转换运算符用作[Widening](../../../visual-basic/language-reference/modifiers/widening.md)如有可能。  
  
## <a name="see-also"></a>请参阅

- [过程](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [过程参数和自变量](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [按值和按引用传递自变量](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [运算符过程](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定义运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [如何：定义转换运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [在 Visual Basic 中的类型转换](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
