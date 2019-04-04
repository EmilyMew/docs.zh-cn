---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814158"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
指定一个或多个声明的局部变量继续存在，并在其中声明它们的过程终止后保留最新值。  
  
## <a name="remarks"></a>备注  
 通常情况下，在过程中的本地变量将消失就立即停止该过程。 静态变量继续存在，并保留其最新值。 你的代码调用该过程，下一次未重新初始化该变量，并且它仍保留分配给它的最新值。 静态变量将继续存在的类或模块中定义的生存期内。  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 可以使用`Static`仅对本地变量。 这意味着声明上下文`Static`变量必须是一个过程或块，在过程中，并且它不能为源文件、 命名空间、 类、 结构或模块。  
  
     不能使用`Static`结构过程内。  
  
-   数据类型的`Static`无法推断局部变量。 有关详细信息，请参阅[本地类型推断](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
-   **组合的修饰符。** 不能指定`Static`连同`ReadOnly`， `Shadows`，或`Shared`同一声明中。  
  
## <a name="behavior"></a>行为  
 当声明中的静态变量`Shared`过程中，只有一个静态变量副本是可用于整个应用程序。 在调用`Shared`过程的方法是使用类名称，不是指向类的实例的变量。  
  
 当声明不是一个过程中的静态变量`Shared`，只有一个变量的副本可为每个类实例。 使用指向类的特定实例的变量调用的非共享过程。  
  
## <a name="example"></a>示例  
 以下示例演示了 `Static` 的用法。  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 `Static`变量`totalSales`仅一次初始化为 0。 你输入每次`updateSales`，`totalSales`仍具有为其计算的最新值。  
  
 `Static`修饰符可用于在此上下文中：  
  
 [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [在 Visual Basic 中的生存期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [变量声明](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
