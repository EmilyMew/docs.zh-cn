---
title: 只能从不带自变量的简单名或限定名中推断匿名类型成员名称
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: b798f296b62b51de34a7ec5ce5a8b608273f5748
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819224"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能从不带自变量的简单名或限定名中推断匿名类型成员名称
无法推断匿名类型成员名称从复杂的表达式。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 有关匿名类型可以和不能推断成员名称和类型从其源的详细信息，请参阅[如何：推断属性名和匿名类型声明中的类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
 **错误 ID:** BC36556  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   将表达式分配到成员名称，如下面的代码中所示：  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>请参阅

- [匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [如何：推断属性名和匿名类型声明中的类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
