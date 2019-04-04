---
title: 构造函数“<name>”不能调用自身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: ef20f74055a07071ef9634973c6852ac58c3143c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824701"
---
# <a name="constructor-name-cannot-call-itself"></a>构造函数\<名称 > 不能调用自身
一个`Sub New`类或结构中的过程调用其自身。  
  
 结构首次创建或构造函数的用途是初始化类的实例。 类或结构可以具有多个构造函数，前提是它们都具有不同的参数列表。 构造函数可以调用另一个构造函数来执行其功能，此外还是其自身。 它是构造函数来调用本身，这对于没有意义，但实际上这会导致无限递归如果允许。  
  
 **错误 ID:** BC30298  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查正在调用的构造函数的参数列表。 它应为不同的构造函数进行调用。  
  
2.  如果您不想要调用的其他构造函数，删除`Sub New`完全调用。  
  
## <a name="see-also"></a>请参阅

- [对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
