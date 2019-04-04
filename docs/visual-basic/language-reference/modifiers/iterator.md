---
title: 迭代器 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822695"
---
# <a name="iterator-visual-basic"></a>迭代器 (Visual Basic)
指定的函数或`Get`访问器是一个迭代器。  
  
## <a name="remarks"></a>备注  
 *迭代器*对集合执行自定义迭代。 迭代器使用[产生](../../../visual-basic/language-reference/statements/yield-statement.md)语句每次在集合中返回每个元素。 当`Yield`达到语句时，保留当前代码中的位置。 下次调用迭代器函数时，将从该位置重新开始执行。  
  
 一个迭代器，可以为函数或作为实现`Get`的属性定义访问器。 `Iterator`修饰符将出现在迭代器函数的声明或`Get`访问器。  
  
 通过使用从客户端代码调用迭代器[为每个...下一条语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 迭代器函数的返回类型或`Get`访问器均可<xref:System.Collections.IEnumerable>， <xref:System.Collections.Generic.IEnumerable%601>， <xref:System.Collections.IEnumerator>，或<xref:System.Collections.Generic.IEnumerator%601>。  
  
 一个迭代器不能有任何`ByRef`参数。  
  
 不能在事件、实例构造函数、静态构造函数或静态析构函数中使用迭代器。  
  
 一个迭代器，可以是匿名函数。 有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="usage"></a>用法  
 `Iterator` 修饰符可用于下面的上下文中：  
  
-   [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>示例  
 下面的示例演示一个迭代器函数。 迭代器函数具有`Yield`内的语句[为...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。 每次迭代[为每个](../../../visual-basic/language-reference/statements/for-each-next-statement.md)在语句体`Main`会调用`Power`迭代器函数。 对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>示例  
 下面的示例演示一个作为迭代器的 `Get` 访问器。 `Iterator`修饰符是属性声明中。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 有关其他示例，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [迭代器](../../programming-guide/concepts/iterators.md)
- [Yield 语句](../../../visual-basic/language-reference/statements/yield-statement.md)
