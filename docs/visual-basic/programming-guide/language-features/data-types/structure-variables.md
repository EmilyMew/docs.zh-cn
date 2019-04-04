---
title: 结构变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816325"
---
# <a name="structure-variables-visual-basic"></a>结构变量 (Visual Basic)
创建结构后，可以将过程级别和模块级变量声明该类型。 例如，可以创建一个结构该记录有关计算机系统的信息。 下面的示例演示这一操作。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 现在可以声明该类型的变量。 下面的声明阐释了这一点。  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  类和模块，请在结构声明使用[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)默认为公共访问。 如果你想要为私有构造函数的结构，请确保将其使用声明[专用](../../../../visual-basic/language-reference/modifiers/private.md)关键字。  
  
## <a name="access-to-structure-values"></a>对结构值的访问  
 若要赋值和检索值的结构变量的元素，您使用相同的语法为用于设置和获取对某个对象的属性。 将成员访问运算符 (`.`) 之间的结构变量名称和元素名称。 以下示例访问以前声明为类型的变量的元素`systemInfo`。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>结构变量赋值  
 如果两者都是相同的结构类型的还可以将一个变量分配到另一个。 这将一个结构的所有元素都复制到其他的相应元素。 下面的声明阐释了这一点。  
  
```  
yourSystem = mySystem  
```  
  
 如果结构元素是引用类型，例如`String`， `Object`，或复制数组，对数据的指针。 在上一示例中，如果`systemInfo`已包含一个对象的变量，则前面的示例将复制从指针`mySystem`到`yourSystem`，和一个结构时，通过该对象的数据的更改都是有效的访问时通过其他结构。  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [复合数据类型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [结构和其他编程元素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [结构和类](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)
