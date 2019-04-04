---
title: 属性“<propertyname>”的“Set”访问器不可访问
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834460"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>Set 访问器属性的\<属性名称 > 不可访问
语句试图存储属性的值不包含属性的访问权限时`Set`过程。  
  
 如果[Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)标记具有限制性更强的访问权限级别比其[Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)，尝试设置属性值在以下情况下可能会失败：  
  
-   `Set`标记语句[专用](../../../visual-basic/language-reference/modifiers/private.md)且调用代码外部的类或结构在其中定义该属性。  
  
-   `Set`标记语句[受保护](../../../visual-basic/language-reference/modifiers/protected.md)，调用代码不在类或结构定义属性，也不在派生类中。  
  
-   `Set`标记语句[友元](../../../visual-basic/language-reference/modifiers/friend.md)并且调用代码不是在其中定义该属性在同一程序集中。  
  
 **错误 ID:** BC31102  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果将属性定义的源代码管理后，请考虑声明`Set`与属性本身相同的访问级别的过程。  
  
-   如果您不能将属性定义的源代码控制，或者您必须限制`Set`过程访问级别的多个属性本身，在尝试将移动到具有更好地访问的代码区域设置的属性值的语句属性。  
  
## <a name="see-also"></a>请参阅

- [属性过程](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [如何：声明具有混合的访问级别的属性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
