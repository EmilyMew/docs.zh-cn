---
title: 没有类的显式实例，就无法从共享方法或共享成员初始值设定项中引用该类的实例成员
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: fc54bbf8053c07cc3b48a762b6f1c60344de9921
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822565"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>没有类的显式实例，就无法从共享方法或共享成员初始值设定项中引用该类的实例成员
已尝试对从共享的过程中的类的非共享成员，请参阅。 下面的示例演示了这种情况。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 在前面的示例中，在赋值语句`x = 10`生成此错误消息。 这是因为共享的过程尝试访问的实例变量。  
  
 在变量`x`是一个实例成员，因为它未声明为[共享](../../../visual-basic/language-reference/modifiers/shared.md)。 类的每个实例`sample`包含其自己单独的变量`x`。 一个实例时设置或更改的值`x`，它不会影响的值`x`中任何其他实例。  
  
 但是，该过程`setX`是`Shared`类的所有实例之间`sample`。 这意味着它不与任何一个类的实例，但而不是独立于单个实例进行操作。 因为它具有与特定实例，没有连接`setX`无法访问一个实例变量。 它必须仅在运行`Shared`变量。 当`setX`设置或更改的新值为可用于类的所有实例的共享变量的值。  
  
 **错误 ID:** BC30369  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  决定要在类的所有实例间共享或保留单独为每个实例的成员。  
  
2.  如果你想要在所有实例间共享的成员的一个副本，添加`Shared`向成员声明关键字。 保留`Shared`过程声明中的关键字。  
  
3.  如果您希望每个实例具有其自己的成员的单独副本，未指定`Shared`成员声明。 删除`Shared`过程声明中的关键字。  
  
## <a name="see-also"></a>请参阅

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
