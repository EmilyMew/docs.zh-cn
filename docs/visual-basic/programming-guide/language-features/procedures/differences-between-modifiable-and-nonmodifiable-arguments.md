---
title: 可修改和不可修改自变量之间的差异 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826660"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>可修改和不可修改自变量之间的差异 (Visual Basic)
在调用过程时，通常向其传递一个或多个自变量。 每个自变量对应于基础编程元素。 基础元素和参数本身可以是可修改或不可修改。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>可修改和不可修改的元素  
 编程元素可以是*可修改的元素*，它可以具有其值已更改，或*不可更改元素*，一旦已创建具有固定的值。  
  
 下表列出了可修改和不可修改的编程元素。  
  
|可修改的元素|不可修改的元素|  
|-------------------------|----------------------------|  
|本地变量 （在过程声明），包括对象变量，包括只读|只读变量、 字段和属性|  
|包括只读字段 （的模块、 类和结构的成员变量）|常量和文本|  
|属性，包括只读|枚举成员|  
|数组元素|表达式 （即使其元素是可修改）|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>可修改和不可修改自变量  
 一个*可修改参数*是另一个使用可修改的基础元素。 调用代码可以将新值存储在任何时候，如果传递参数[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，过程中的代码还可以修改调用代码中的基础元素。  
  
 一个*不可修改自变量*具有不可修改的基础元素或传递[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 该过程不能修改调用代码中的基础元素，即使它是可修改的元素。 如果它是不可修改的元素，调用代码本身不能修改它。  
  
 被调用的过程可能会修改其不可修改的参数的本地副本，但修改不会影响调用代码中的基础元素。  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [通过值传递自变量和通过引用传递自变量之间的差异](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：更改过程自变量的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
