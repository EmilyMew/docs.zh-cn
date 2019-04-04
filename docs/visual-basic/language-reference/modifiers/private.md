---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819471"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
指定一个或多个声明的编程元素中包含的任何类型包括从其声明上下文中只能从可访问。  
  
## <a name="remarks"></a>备注  
 如果编程元素表示专有的功能，或包含机密数据，你通常想要尽可能严格限制对它的访问。 模块、 类或结构，它定义其进行访问，从而实现最大限制。 若要限制到这种方式中的元素的访问，可将其与声明`Private`。  

> [!NOTE]
> 此外可以使用[Private Protected](private-protected.md)访问修饰符，使成员可访问从使该类中和从派生类中包含的程序集。

## <a name="rules"></a>规则  

-   **声明上下文。** 只能在模块级别使用 `Private`。 这意味着声明上下文`Private`元素必须是模块、 类或结构，并且不能为源文件、 命名空间、 接口或过程。  
  
## <a name="behavior"></a>行为  
  
-   **访问级别。** 声明上下文中的所有代码可以都访问其`Private`元素。 这包括所包含的类型，例如嵌套的类或枚举中的赋值表达式中的代码。 声明上下文以外的任何代码可以访问其`Private`元素。  
  
-   **访问修饰符。** 指定的访问级别的关键字称为*访问修饰符*。 访问修饰符的比较，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Private` 修饰符可用于下面的上下文中：  
  
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
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- [受保护的友元](./protected-friend.md)[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [过程](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
