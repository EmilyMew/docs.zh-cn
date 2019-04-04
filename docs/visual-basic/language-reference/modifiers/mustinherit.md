---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816559"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
指定一个类可以仅用作基类，则不能直接从其中创建对象。  
  
## <a name="remarks"></a>备注  
 目的*基类*(也称为*抽象类*) 是定义普遍适用于从其派生的所有类的功能。 这使派生的类无需重新定义的常用元素。 在某些情况下，此通用功能不是足够完整，从而使可用对象，并每个派生的类定义缺少的功能。 在这种情况下，您希望使用的代码只能从派生类中创建对象。 您使用`MustInherit`上强制实施此的基类。  
  
 另一个用途`MustInherit`类是限制对一组相关的类的变量。 您可以定义一个基类，并从其派生所有这些相关的类。 基类不需要提供任何功能普遍适用于所有派生的类，但它可用作筛选器将值分配到变量。 如果你使用的代码声明一个变量，作为类的基类，Visual Basic，可从派生类之一仅对象分配给该变量。  
  
 .NET Framework 定义了多个`MustInherit`类，在它们之间<xref:System.Array>， <xref:System.Enum>，和<xref:System.ValueType>。 <xref:System.ValueType> 是一个基类，它将限制变量的示例。 所有值类型都派生<xref:System.ValueType>。 如果你声明一个变量，作为<xref:System.ValueType>，可以将只有值类型分配给该变量。  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 可以使用`MustInherit`仅在`Class`语句。  
  
-   **组合的修饰符。** 不能指定`MustInherit`一起使用`NotInheritable`同一声明中。  
  
## <a name="example"></a>示例  
 下面的示例演示强制的继承和强制重写。 类的基类`shape`定义一个变量， `acrossLine`。 类`circle`并`square`派生自`shape`。 它们继承的定义`acrossLine`，但它们必须定义该函数`area`因为该计算不同的形状的每一类。  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 您可以声明`shape1`并`shape2`属于类型`shape`。 但是，不能创建一个对象从`shape`因为它缺少函数的功能`area`将标记为`MustInherit`。  
  
 因为它们被声明为`shape`，变量`shape1`并`shape2`仅限于从派生类的对象`circle`和`square`。 Visual Basic 不允许您将任何其他对象分配给这些变量，它为您提供了类型安全的高级别。  
  
## <a name="usage"></a>用法  
 `MustInherit`修饰符可用于在此上下文中：  
  
 [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Inherits 语句](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
