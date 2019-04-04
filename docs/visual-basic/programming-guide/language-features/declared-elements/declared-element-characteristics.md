---
title: 已声明元素的特性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 98f6a7738a462e9f36abdc0380cb1fe8d488fb9d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821291"
---
# <a name="declared-element-characteristics-visual-basic"></a>已声明元素的特性 (Visual Basic)
一个*特征*的已声明的元素是代码与它的交互方式会影响该元素的一个方面。 每个已声明的元素具有一个或多个与之关联的以下特征：  
  
-   *数据类型*— 元素可以持有的值，以及它如何存储这些值。 有关详细信息，请参阅[数据类型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
-   *生存期*— 在此期间的元素是可供使用的执行时间段。 有关详细信息，请参阅[在 Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   *作用域*-的所有代码都可以引用而没有限定其名称的元素集。 有关详细信息，请参阅[如何：控制变量的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)。  
  
-   *访问级别*— 代码来实现的权限元素的使用。 有关详细信息，请参阅[如何：控制变量的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>元素的特性  
 下表显示了已声明的元素和将应用于每个特征。  
  
|元素|数据类型|生存期|作用域<sup>1</sup>|访问级别|  
|-------------|---------------|--------------|------------------------|------------------|  
|变量|是|是|是|是|  
|返回的常量|是|No|是|是|  
|枚举|是|No|是|是|  
|结构|否|否|是|是|  
|属性|是|是|是|是|  
|方法|否|是|是|是|  
|过程 (`Sub`或`Function`)|否|是|是|是|  
|过程参数|是|是|是|否|  
|函数返回|是|是|是|否|  
|运算符|是|No|是|是|  
|接口|否|否|是|是|  
|类|否|否|是|是|  
|Event|否|否|是|是|  
|委托|否|否|是|是|  
  
 <sup>1</sup>作用域有时称为*可见性*。  
  
## <a name="see-also"></a>请参阅

- [已声明的元素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [在 Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
