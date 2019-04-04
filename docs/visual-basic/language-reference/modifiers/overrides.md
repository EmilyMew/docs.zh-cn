---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826582"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
指定某一属性或过程可重写从基类中继承的具有相同名称的属性或过程。  
  
## <a name="remarks"></a>备注  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 只能在属性或过程声明语句中使用 `Overrides`。  
  
-   **组合的修饰符。** 不能在同一过程声明中同时指定 `Overrides` 和 `Shadows` 或 `Shared`。 由于重写元素是隐式可重写的，因此不能将 `Overridable` 与 `Overrides` 组合到一起。  
  
-   **匹配的签名。** 此声明的签名必须完全匹配*签名*属性或过程，它会重写。 这意味着参数列表必须具有相同数量的参数，并且排序顺序和数据类型都必须完全相同。  
  
     除签名外，重写的声明还必须完全匹配以下项：  
  
    -   访问级别  
  
    -   返回类型（如有）  
  
-   **泛型签名。** 对于泛型过程，签名包括类型参数的数量。 因此，重写的声明必须在这方面与基类版本匹配。  
  
-   **附加匹配。** 除匹配基类版本的签名外，此声明还必须在以下方面与其匹配：  
  
    -   访问级别修饰符 (如[公共](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   传递的每个参数的机制 ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   泛型过程的每个类型参数的约束列表  
  
-   **隐藏和重写。** 隐藏和重写操作都可重新定义继承的元素，但这两种方法之间又具有很大的差异。 有关详细信息，请参阅[Visual Basic 中的隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 如果使用 `Overrides`，编译器将隐式添加 `Overloads`，以便库 API 更轻松地使用 C#。  
  
 `Overrides` 修饰符可用于下面的上下文中：  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [在 Visual Basic 中隐藏](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [类型列表](../../../visual-basic/language-reference/statements/type-list.md)
