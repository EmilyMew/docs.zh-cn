---
title: 如何：将对象声明使用对象初始值设定项 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 314706207800b2e86aa0032a52d8c50fbb726887
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825127"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>如何：将对象声明使用对象初始值设定项 (Visual Basic)
对象初始值设定项，可以声明并实例化单个语句中类的实例。 此外，可以不调用参数化构造函数的情况下一次初始化实例的一个或多个成员。  
  
 当使用对象初始值设定项来创建已命名类型的实例时，将调用类的默认构造函数，跟您指定的顺序的指定成员的初始化。  
  
 下面的过程演示如何创建的实例`Student`三种不同方式的类。 类具有名字、 姓氏和类年属性，等等。 三个声明的每个创建的新实例`Student`，使用属性`First`设置为"Michael"，属性`Last`设置为"Tucker"，并且所有其他成员设置为其默认值。 在过程中每个声明的结果等效于以下示例中，不使用对象初始值设定项。  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 实现`Student`类，请参阅[如何：创建的项列表](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。 可以将代码复制从该主题设置类并创建一系列`Student`要使用的对象。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>若要使用对象初始值设定项创建的已命名的类对象  
  
1.  开始声明，因为如果您计划使用的构造函数。  
  
     `Dim student1 As New Student`  
  
2.  键入的关键字`With`后, 跟一个大括号括起来的初始化列表。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  在初始化列表中，包括每个属性，你想要初始化并向其分配初始值。 属性的名称以句点开头。  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     您可以初始化类的一个或多个成员。  
  
4.  或者，可以声明类的新实例，然后将值分配给它。 首先，声明的实例`Student`:  
  
     `Dim student2 As Student`  
  
5.  开始创建的实例`Student`以正常方式。  
  
     `Dim student2 As Student = New Student`  
  
6.  类型`With`，然后对象初始值设定项的新实例的一个或多个成员进行初始化。  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  你可以通过省略来简化上一步中的定义`As Student`。 如果这样做，编译器确定`student3`的一个实例`Student`使用局部类型推理。  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     有关详细信息，请参阅[本地类型推断](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
## <a name="see-also"></a>请参阅

- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [如何：创建的项的列表](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [对象初始值设定项：命名和匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
