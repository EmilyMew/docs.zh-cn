---
title: 属性“<propertyname>”的“Get”访问器不可访问
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 8fb78f3c14708c79f1910e202287c25a3b2213b7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814401"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>Get 访问器属性的\<属性名称 > 不可访问
语句试图检索属性的值不包含属性的访问权限时`Get`过程。  
  
 如果[Get 语句](../../../visual-basic/language-reference/statements/get-statement.md)标记具有限制性更强的访问权限级别比其[Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)，尝试读取属性值在以下情况下可能会失败：  
  
-   `Get`标记语句[专用](../../../visual-basic/language-reference/modifiers/private.md)且调用代码外部的类或结构在其中定义该属性。  
  
-   `Get`标记语句[受保护](../../../visual-basic/language-reference/modifiers/protected.md)，调用代码不在类或结构定义属性，也不在派生类中。  
  
-   `Get`标记语句[友元](../../../visual-basic/language-reference/modifiers/friend.md)并且调用代码不是在其中定义该属性在同一程序集中。  
  
 **错误 ID:** BC31103  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果将属性定义的源代码管理后，请考虑声明`Get`与属性本身相同的访问级别的过程。  
  
-   如果您不能将属性定义的源代码控制，或者您必须限制`Get`过程访问级别的多个属性本身，试着继续读取属性值设置为更好地访问某个区域的代码的语句属性。  
  
## <a name="see-also"></a>请参阅

- [属性过程](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [如何：声明具有混合的访问级别的属性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
