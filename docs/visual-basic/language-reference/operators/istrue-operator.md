---
title: IsTrue 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: cb8ad8cb4a1ec13611edfcc3de7f4b7eb33fc553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829923"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 运算符 (Visual Basic)
确定表达式是否为`True`。  
  
 不能调用`IsTrue`显式中你的代码，而 Visual Basic 编译器可以使用它来生成代码从`OrElse`子句。 如果你定义类或结构，然后使用在该类型的变量`OrElse`子句，则必须定义`IsTrue`类或结构上。  
  
 编译器会考虑`IsTrue`并`IsFalse`作为运算符*匹配对*。 这意味着，如果其中一个定义，您还必须定义另一个。  
  
## <a name="compiler-use-of-istrue"></a>为 true 时的编译器使用  
 如果已定义类或结构，可以使用中该类型的变量`For`， `If`， `Else If`，或`While`语句，或在`When`子句。 如果这样做，则编译器会要求将转换到类型的运算符`Boolean`值以便可以测试条件。 它会搜索合适的运算符按以下顺序：  
  
1.  在类或结构的扩大转换运算符`Boolean`。  
  
2.  在类或结构的扩大转换运算符`Boolean?`。  
  
3.  `IsTrue`运算符在类或结构上的。  
  
4.  收缩转换到`Boolean?`，并不涉及从转换`Boolean`到`Boolean?`。  
  
5.  在类或结构的收缩转换运算符`Boolean`。  
  
 如果您未定义任何转换为`Boolean`或`IsTrue`运算符，编译器会引发错误。  
  
> [!NOTE]
>  `IsTrue`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，其操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例定义一个结构，其中包含定义大纲`IsFalse`和`IsTrue`运算符。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>请参阅

- [IsFalse 运算符](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [如何：定义运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse 运算符](../../../visual-basic/language-reference/operators/orelse-operator.md)
