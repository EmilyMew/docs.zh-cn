---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822812"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
指定属性或过程未实现此类中，必须重写派生类中，然后才能使用。  
  
## <a name="remarks"></a>备注  
 只能在属性或过程声明语句中使用 `MustOverride`。 属性或过程的指定`MustOverride`必须是类的成员，类必须标记[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。  
  
## <a name="rules"></a>规则  
  
-   **不完整的声明。** 当指定`MustOverride`，不会不提供任何其他代码行的属性或过程，即使`End Function`， `End Property`，或`End Sub`语句。  
  
-   **组合的修饰符。** 不能指定`MustOverride`连同`NotOverridable`， `Overridable`，或`Shared`同一声明中。  
  
-   **隐藏和重写。** 隐藏和重写操作都可重新定义继承的元素，但这两种方法之间又具有很大的差异。 有关详细信息，请参阅[Visual Basic 中的隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
-   **替换术语。** 除不能用作重写中的元素有时称为*纯虚拟*元素。  
  
 `MustOverride` 修饰符可用于下面的上下文中：  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [在 Visual Basic 中隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
