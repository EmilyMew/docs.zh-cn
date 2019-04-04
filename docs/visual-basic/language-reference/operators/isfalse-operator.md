---
title: IsFalse 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 9f25c406038486224c2c4708c86ef86889c44c15
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818483"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 运算符 (Visual Basic)
确定表达式是否为`False`。  
  
 不能调用`IsFalse`显式中你的代码，而 Visual Basic 编译器可以使用它来生成代码从`AndAlso`子句。 如果你定义类或结构，然后使用在该类型的变量`AndAlso`子句，则必须定义`IsFalse`类或结构上。  
  
 编译器会考虑`IsFalse`并`IsTrue`作为运算符*匹配对*。 这意味着，如果其中一个定义，您还必须定义另一个。  
  
> [!NOTE]
>  `IsFalse`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，其操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例定义一个结构，其中包含定义大纲`IsFalse`和`IsTrue`运算符。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>请参阅

- [IsTrue 运算符](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [如何：定义运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 运算符](../../../visual-basic/language-reference/operators/andalso-operator.md)
