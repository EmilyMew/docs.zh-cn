---
title: Default (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836722"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
一个属性标识为其类、 结构或接口的默认属性。  
  
## <a name="remarks"></a>备注  
 类、 结构或接口可以将最多一个作为其属性的指定*默认属性*，前提是该属性带有至少一个参数。 如果代码而无需指定成员的类或结构的引用，Visual Basic 解析到的默认属性的引用。  
  
 默认属性可能会导致小减少源代码的字符，但它们会使代码更难以阅读。 如果发出对类或结构名称的引用时，调用代码不熟悉你的类或结构，它无法确定该引用访问的类或结构本身或默认属性。 这可能会导致编译器错误或细微的运行时逻辑错误。  
  
 您可以始终使用某种程度上减少默认属性错误的可能性[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)设置编译器类型检查到`On`。  
  
 如果想要使用预定义的类或结构在代码中，您必须确定是否具有默认属性，以及如果成功，其名称是什么。  
  
 由于这些缺点，应考虑未定义默认属性。 代码的可读性，应该还考虑始终显式引用的所有属性，包括默认属性。  
  
 `Default`修饰符可用于在此上下文中：  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>请参阅

- [如何：声明并在 Visual Basic 中调用默认属性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
