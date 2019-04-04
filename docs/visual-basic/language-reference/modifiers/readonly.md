---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825386"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
指定的可读取但不是会写入变量或属性。  
  
## <a name="remarks"></a>备注  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 只能在模块级别使用 `ReadOnly`。 这意味着声明上下文`ReadOnly`元素必须是类、 结构或模块，并且不能是源文件、 命名空间或过程。  
  
-   **组合的修饰符。** 不能指定`ReadOnly`一起使用`Static`同一声明中。  
  
-   **分配一个值。** 代码使用`ReadOnly`属性不能将其值设置。 但是，有权访问基础存储的代码可以分配或在任何时间更改的值。  
  
     可以将值赋给`ReadOnly`变量仅在其声明中或在类或结构在其中定义的构造函数中。  
  
## <a name="when-to-use-a-readonly-variable"></a>何时使用只读变量  
 在有些情况下，不能使用[Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)来声明和分配常量值。 例如，`Const`语句可能不接受的数据类型，你想要分配，或您可能不能在编译时使用的常量表达式计算的值。 您可能甚至不知道值在编译时。 在这些情况下，你可以使用`ReadOnly`变量来保存常量值。  
  
> [!IMPORTANT]
>  即使变量本身是引用类型，如数组或类实例，该变量的数据类型是否可以更改其成员`ReadOnly`。 下面的示例阐释了这一点。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 在初始化时，该数组由指向`characterArray()`包含"x"、"y"和"z"。 因为变量`characterArray`是`ReadOnly`，只要该函数将初始化; 即，不能更改其值，不能为其分配一个新数组。 但是，您可以更改一个或多个数组成员的值。 过程调用后面`changeArrayElement`，指向的数组`characterArray()`包含"x"、"M"和"z"。  
  
 请注意，这是类似于声明过程参数为[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)，这阻止过程调用参数本身进行更改，但允许它以更改其成员。  
  
## <a name="example"></a>示例  
 下面的示例定义`ReadOnly`雇佣员工的日期的属性。 类存储的属性值在内部作为`Private`变量，并且仅在类中的代码可以更改此值。 但是，该属性是`Public`，并可以访问的类的任何代码可以读取该属性。  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` 修饰符可用于下面的上下文中：  
  
 [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>请参阅

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
