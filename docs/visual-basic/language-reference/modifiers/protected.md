---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 88e13fcd03c6a10cf1450cec90f9ca60aedc3eb1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819159"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
指定一个或多个声明编程元素的成员访问修饰符只能从来访问其自己的类中或从派生类。  
  
## <a name="remarks"></a>备注  
 有时，在类中声明的编程元素包含敏感数据或受限制的代码，并且你想要限制对元素的访问。 但是，如果类是可继承，并预计的派生类层次结构，它可能需要这些派生的类来访问数据或代码。 在这种情况下，想要从基本类和所有派生类可访问的元素。 若要限制到这种方式中的元素的访问，可将其与声明`Protected`。  

> [!NOTE]
> `Protected`访问修饰符可以结合这两个其他修饰符：
> - [Protected Friend](protected-friend.md)修饰符使类成员在该类中，从派生类中，和在其中定义类的相同程序集内访问。 
> - [Private Protected](private-protected.md)修饰符使类成员可访问由派生类型，但只能在其包含程序集内。
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 可以使用`Protected`仅在类级别。 这意味着声明上下文`Protected`元素必须是类，且不能为源文件、 命名空间、 接口、 模块、 结构或过程。  

## <a name="behavior"></a>行为  
  
-   **访问级别。** 在类中的所有代码可以都访问它的元素。 从基类派生的任何类中的代码可以访问所有`Protected`元素的基类。 这是派生的针对每一代，则返回 true。 这意味着，一个类可以访问`Protected`元素的基类的基类，依次类推。  
  
     受保护的访问不是超集或友元访问权限的子集。  
  
-   **访问修饰符。** 指定的访问级别的关键字称为*访问修饰符*。 访问修饰符的比较，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Protected` 修饰符可用于下面的上下文中：  
  
 [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 语句](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [在 Visual Basic 中的访问级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [过程](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
