---
title: 使用字符串名调用属性或方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: e267c0c4d1d3e8f986348863d933c984f686b33b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842637"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>使用字符串名调用属性或方法 (Visual Basic)
在大多数情况下，可以在设计时发现的属性和方法的一个对象，并编写代码来处理它们。 但是，在某些情况下您可能事先不知道有关对象的属性和方法，或者您可能只是想启用最终用户可以指定属性或在运行时执行方法的灵活性。  
  
## <a name="callbyname-function"></a>CallByName 函数  
 例如，考虑通过将运算符传递给 COM 组件的用户输入的表达式的计算结果的客户端应用程序。 假设您正在向组件需要新的运算符的不断添加新的函数。 当使用标准的对象的访问技术时，必须重新编译和重新分发客户端应用程序，可以使用新的运算符之前。 若要避免此问题，可以使用`CallByName`函数的新运算符作为字符串来传递，而无需更改应用程序。  
  
 `CallByName`函数允许您使用一个字符串，在运行时指定的属性或方法。 签名`CallByName`函数如下所示：  
  
 *结果* = `CallByName`(*对象*，*过程名称*， *CallType*，*参数*（)）  
  
 第一个参数，*对象*，采用你想要对其执行操作的对象的名称。 *过程名称*参数采用一个字符串，包含要调用的方法或属性过程的名称。 *CallType*参数采用一个常量，它表示要调用过程的类型： 一种方法 (`Microsoft.VisualBasic.CallType.Method`)，读取的属性 (`Microsoft.VisualBasic.CallType.Get`)，或设置一个属性 (`Microsoft.VisualBasic.CallType.Set`)。 *自变量*参数，这是可选的采用的类型数组`Object`，其中包含任何参数的过程。  
  
 可以使用`CallByName`类在您当前的解决方案，但它是最常用于访问 COM 对象或对象从[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]程序集。  
  
 假设您添加对包含一个名为类的程序集的引用`MathClass`，其中包含一个名为的新函数`SquareRoot`，如下面的代码中所示：  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 你的应用程序可以使用文本框控件来控制将调用哪些方法和其参数。 例如，如果`TextBox1`包含要计算的表达式并`TextBox2`是用于输入的函数的名称，可以使用以下代码来调用`SquareRoot`函数中的表达式`TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 如果在输入"64" `TextBox1`，"SquareRoot"中的`TextBox2`，然后调用`CallMath`过程中，数字的平方根`TextBox1`进行评估。 在示例代码会调用`SquareRoot`函数 （采用一个字符串，包含要评估为必需的参数的表达式），并返回"8"中`TextBox1`（64 的平方根）。 当然，如果用户输入中的无效字符串`TextBox2`，如果该字符串包含名称的属性而不是一种方法，或如果该方法具有一个额外的必需的参数，会发生运行时错误。 您必须使用时添加可靠的错误处理代码`CallByName`以应对预期的这些或任何其他错误。  
  
> [!NOTE]
>  虽然`CallByName`函数可能会在某些情况下很有用，您必须权衡对性能产生影响其有用性 — 使用`CallByName`调用的过程是比后期绑定调用稍慢。 如果所调用的函数被重复调用，例如在循环中，如`CallByName`会对性能产生严重。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [确定对象类型](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
