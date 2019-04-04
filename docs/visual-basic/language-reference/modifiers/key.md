---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842299"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
`Key`关键字，可以指定属性的匿名类型的行为。 只有属性指定为键属性的匿名类型实例或计算的哈希代码值之间的相等性测试中。 不能更改键属性的值。  
  
 将匿名类型的属性为键属性指定放置关键字`Key`其声明的初始化列表中的前面。 在以下示例中，`Airline`并`FlightNo`是键属性，但`Gate`不是。  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 创建新的匿名类型时，它直接继承自<xref:System.Object>。 编译器重写继承的三个成员： <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 为生成的重写代码<xref:System.Object.Equals%2A>和<xref:System.Object.GetHashCode%2A>基于键属性。 如果在类型中，没有键属性<xref:System.Object.GetHashCode%2A>和<xref:System.Object.Equals%2A>未重写。  
  
## <a name="equality"></a>相等  
 匿名类型的两个实例相等，如果它们是相同类型的实例，其键属性的值是否相等。 在以下示例中，`flight2`等同于`flight1`上一示例中因为它们是实例的同一匿名类型，它们有匹配的值的它们的键属性。 但是，`flight3`不等于`flight1`因为它具有不同的值的键属性， `FlightNo`。 实例`flight4`不是相同的类型`flight1`因为它们将不同的属性指定为键属性。  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 如果两个实例声明仅具有非键属性，名称、 类型、 顺序和值，在相同的两个实例不相等。 实例键属性不是只等于其自身。  
  
 有关在其下两个匿名类型实例是同一匿名类型的实例的条件的详细信息，请参阅[匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="hash-code-calculation"></a>哈希代码计算  
 像<xref:System.Object.Equals%2A>，在中定义的哈希函数<xref:System.Object.GetHashCode%2A>匿名类型根据类型的键属性。 下面的示例显示键属性和哈希之间的交互的代码值。  
  
 具有相同的值的所有键属性的匿名类型的实例具有相同的哈希代码值，即使非键属性没有匹配的值。 下面的语句返回`True`。  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 具有不同的一个或多个键属性的值的匿名类型的实例具有不同的哈希代码值。 下面的语句返回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 将不同的属性指定为键属性的匿名类型的实例不是同一类型的实例。 即使名称和所有属性的值是相同的它们具有不同的哈希代码值。 下面的语句返回`False`。  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>只读的值  
 不能更改键属性的值。 例如，在`flight1`前面的示例中，`Airline`并`FlightNo`字段是只读的但`Gate`可以更改。  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>请参阅

- [匿名类型定义](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [如何：推断属性名和匿名类型声明中的类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
