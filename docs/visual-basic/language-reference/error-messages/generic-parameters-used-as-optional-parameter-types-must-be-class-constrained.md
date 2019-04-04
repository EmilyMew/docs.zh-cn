---
title: 用作可选参数类型的泛型参数必须受类约束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813894"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>用作可选参数类型的泛型参数必须受类约束
使用可选参数使用不受约束为引用类型的类型参数声明的过程。  
  
 您必须始终提供每个可选参数的默认值。 如果参数为引用类型，可选的值必须为`Nothing`，这是对于任何引用类型的有效值。 但是，如果该参数的值类型，该类型必须是预定义的 Visual basic 的基本数据类型。 这是因为复合值类型，例如，用户定义的结构，有没有有效默认值。  
  
 当您使用的类型参数为可选参数时，必须保证它属于引用类型以避免包含任何有效的默认值的值类型的可能性。 这意味着必须使用约束类型参数`Class`关键字或具有特定类的名称。  
  
 **错误 ID:** BC32124  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   约束类型参数以接受仅为引用类型，或不使用它为可选参数。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [类型列表](../../../visual-basic/language-reference/statements/type-list.md)
- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [可选参数](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
