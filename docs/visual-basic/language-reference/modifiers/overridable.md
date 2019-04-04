---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816871"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
指定的属性或过程可以替代的具有相同名称的属性或在派生类中的过程。  
  
## <a name="remarks"></a>备注  
 `Overridable`修饰符类在派生类中重写中允许的属性或方法。 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修饰符可阻止属性或方法在派生类中重写。  有关详细信息，请参阅[继承基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果`Overridable`或`NotOverridable`修饰符未指定，默认设置取决于是否属性或方法重写基类属性或方法。 如果属性或方法重写基类属性或方法，默认设置是`Overridable`; 否则为它是`NotOverridable`。  
  
 您可以通过隐藏或重写要重新定义继承的元素，但有两种方法之间的重大差别。 有关详细信息，请参阅[Visual Basic 中的隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 可以重写的元素有时称为*虚拟*元素。 如果它可以重写，但不一定要有时也称为*具体*元素。  
  
 只能在属性或过程声明语句中使用 `Overridable`。  
  
## <a name="combined-modifiers"></a>组合的修饰符  
 不能指定`Overridable`或`NotOverridable`为`Private`方法。  
  
 不能指定`Overridable`连同`MustOverride`， `NotOverridable`，或`Shared`同一声明中。  
  
 由于重写元素是隐式可重写的，因此不能将 `Overridable` 与 `Overrides` 组合到一起。  
  
## <a name="usage"></a>用法  
 `Overridable` 修饰符可用于下面的上下文中：  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [修饰符](../../../visual-basic/language-reference/modifiers/index.md)
- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [在 Visual Basic 中隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
