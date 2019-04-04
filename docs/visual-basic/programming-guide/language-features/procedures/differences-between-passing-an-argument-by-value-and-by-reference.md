---
title: 通过值传递参数和通过引用传递参数之间的差异 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837487"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>通过值传递参数和通过引用传递参数之间的差异 (Visual Basic)
当将一个或多个自变量传递给过程中时，每个自变量对应于调用代码中的基础编程元素。 可以传递此基础元素的值，或者对它的引用。 这称为*传递机制*。  
  
## <a name="passing-by-value"></a>按值传递  
 传递参数*按值*通过指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)过程定义中的相应参数的关键字。 当使用此传递机制时，Visual Basic 将基础编程元素的值复制到该过程中的本地变量。 过程代码中调用代码没有任何对基础元素的访问。  
  
## <a name="passing-by-reference"></a>按引用传递  
 传递参数*通过引用*通过指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)过程定义中的相应参数的关键字。 当使用此传递机制时，Visual Basic 使过程对基础编程元素的直接引用中调用代码。  
  
## <a name="passing-mechanism-and-element-type"></a>传递机制和元素类型  
 选择的传递机制不是相同的基础元素类型的分类。 按值或按引用传递引用 Visual Basic 提供的过程代码。 值类型或引用类型引用的编程元素在内存中的存储方式。  
  
 但是，传递机制和元素类型是相互关联。 引用类型的值是指向内存中其他位置的数据。 这意味着当通过值传递引用类型，过程代码具有指向基础元素的数据，即使它不能访问基础元素本身也是如此。 例如，如果该元素为数组变量，过程代码不具有访问该变量本身，但它可以访问的数组成员。  
  
## <a name="ability-to-modify"></a>若要修改的功能  
 时作为参数传递不可修改的元素，该过程可以永远不能修改它调用代码中是否超过`ByVal`或`ByRef`。  
  
 对于可修改的元素下, 表总结了元素类型和传递机制之间的交互。  
  
|元素类型|传递 `ByVal`|传递 `ByRef`|  
|------------------|--------------------|--------------------|  
|值类型 （只包含一个值）|该过程不能更改该变量或其任何成员。|该过程可以更改变量和其成员。|  
|引用类型 （包含的类或结构实例的指针）|该过程不能更改该变量，但可以更改它所指向的实例的成员。|该过程可以更改变量和它所指向的实例的成员。|  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [如何：将参数传递给过程](./how-to-pass-arguments-to-a-procedure.md)
- [按值和按引用传递自变量](./passing-arguments-by-value-and-by-reference.md)
- [可修改和不可修改自变量之间的差异](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [如何：更改过程自变量的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止过程自变量的值更改](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：强制通过值传递自变量](./how-to-force-an-argument-to-be-passed-by-value.md)
- [按位置和按名称传递自变量](./passing-arguments-by-position-and-by-name.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
