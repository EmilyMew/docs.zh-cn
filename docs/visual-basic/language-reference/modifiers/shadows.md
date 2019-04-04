---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: c314db90a1a0f89613e20897387bdec8ec534837
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834135"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
指定声明的编程元素重新声明并隐藏具有相同名称的元素或在基类中的重载元素集。  
  
## <a name="remarks"></a>备注  
 隐藏的主要目的 (也称为*按名称隐藏*) 是保留的类成员定义。 基本类可能需要进行更改，创建具有作为一个已定义的相同名称的元素。 如果发生这种情况，`Shadows`通过您的类将解析为成员的修饰符强制引用你定义，而不是新基类元素。  
  
 隐藏和重写操作都可重新定义继承的元素，但这两种方法之间又具有很大的差异。 有关详细信息，请参阅[Visual Basic 中的隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 可以使用`Shadows`仅在类级别。 这意味着声明上下文`Shadows`元素必须是类，且不能为源文件、 命名空间、 接口、 模块、 结构或过程。  
  
     您可以声明在单个声明语句中只能有一个隐藏的元素。  
  
-   **组合的修饰符。** 不能指定`Shadows`连同`Overloads`， `Overrides`，或`Static`同一声明中。  
  
-   **元素类型。** 可以与任何其他类型一起隐藏任何类型的已声明元素。 如果隐藏属性或使用另一个属性或过程的过程，参数和返回类型无需与基类属性或过程中的匹配。  
  
-   **访问。** 通常情况下隐藏它的派生类中从无法在基类中隐藏的元素。 但是，以下注意事项适用。  
  
    -   如果不能从引用它的代码访问隐藏的元素，该引用被解析为隐藏的元素。 例如，如果`Private`元素将隐藏基类元素，不具有访问权限的代码`Private`元素将改为访问的基类元素。  
  
    -   如果隐藏某个元素时，仍可以通过使用基类的类型声明的对象来访问隐藏的元素。 您还可以访问通过`MyBase`。  
  
 `Shadows` 修饰符可用于下面的上下文中：  
  
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

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [重载](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [在 Visual Basic 中隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
