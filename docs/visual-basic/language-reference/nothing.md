---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 97c651dbcc657fbab0706c9a959bd0031c0fe343
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826088"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
表示任何数据类型的默认值。 对于引用类型，默认值是`null`引用。 对于值类型，默认值取决于值类型是否可以为 null。  
  
> [!NOTE]
>  对于不可为 null 的值类型，`Nothing`在 Visual Basic 中不同于`null`中C#。 在 Visual Basic 中，如果设置为非空值类型的变量`Nothing`，变量设置为其声明的类型的默认值。 在C#，如果将分配到非空值类型的变量`null`，则发生编译时错误。  
  
## <a name="remarks"></a>备注  
 `Nothing` 表示一种数据类型的默认值。 默认值取决于该变量是值类型的类型或引用类型。  
  
 变量*值类型*直接包含它的值。 值类型包括所有数值数据类型， `Boolean`， `Char`， `Date`，所有结构和所有枚举。 变量*引用类型*在内存中存储对对象的实例的引用。 引用类型包括类、 数组、 委托，以及字符串。 有关更多信息，请参见 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
 如果变量是值类型的行为`Nothing`取决于该变量是可以为 null 的数据类型。 若要表示为空值类型，将添加`?`修饰符的类型名称。 将分配`Nothing`给可以为 null 的变量的值设置为`null`。 有关详细信息和示例，请参阅[可以为 Null 的值类型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。  
  
 如果变量是不可为 null 的值类型，分配给`Nothing`到它将其设置为默认值为其声明的类型。 如果该类型包含变量的成员，它们都设置为其默认值。 下面的示例阐释了这一点对于标量类型。  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 如果引用类型的变量，将分配`Nothing`为该变量设置它为`null`变量的类型的引用。 设置为一个变量`null`引用不与任何对象相关联。 下面的示例演示这一操作。  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 检查变量是否引用 （或可以为 null 的值类型） 时`null`，请不要使用`= Nothing`或`<> Nothing`。 始终使用`Is Nothing`或`IsNot Nothing`。  
  
 对于在 Visual Basic 中的字符串，则为空字符串等于`Nothing`。 因此，`"" = Nothing`为 true。  
  
 下面的示例演示使用的比较`Is`和`IsNot`运算符。  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 如果不使用声明一个变量`As`子句并将其设置为`Nothing`，该变量的类型为`Object`。 此示例是`Dim something = Nothing`。 在这种情况下发生编译时错误时`Option Strict`位于和`Option Infer`处于关闭状态。  
  
 在分配`Nothing`给对象变量，它不再引用任何对象实例。 如果对象之前引用了一个实例，则将其设置为`Nothing`不会终止该实例本身。 终止该实例，并释放与之关联的内存和系统资源，只有在垃圾回收器 (GC) 检测到有任何活动的引用后。  
  
 `Nothing` 不同于<xref:System.DBNull>对象，表示未初始化的变量或不存在的数据库列。  
  
## <a name="see-also"></a>请参阅

- [Dim 语句](../../visual-basic/language-reference/statements/dim-statement.md)
- [对象生存期：如何创建和销毁对象](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [在 Visual Basic 中的生存期](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is 运算符](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 运算符](../../visual-basic/language-reference/operators/isnot-operator.md)
- [可以为 null 的值类型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
