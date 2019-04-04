---
title: 宽松委托转换 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 57e863d9781721a997ae49e1a5c9d8f3562a1bd0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842715"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>宽松委托转换 (Visual Basic)
宽松的委托转换，可将子例程和函数分配给委托或处理程序，即使它们的签名不相同。 因此，绑定到委托将与已允许为方法调用的绑定一致。  
  
## <a name="parameters-and-return-type"></a>参数和返回类型  
 替代签名完全匹配，宽松的转换需要满足以下条件时`Option Strict`设置为`On`:  
  
-   扩大转换为已分配的函数的相应参数的数据类型必须存在从每个委托参数的数据类型或`Sub`。 在下面的示例中，委托`Del1`具有一个参数、 `Integer`。 参数`m`中已分配的 lambda 表达式必须具有的扩大转换的数据类型`Integer`，如`Long`或`Double`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     允许收缩转换时，才`Option Strict`设置为`Off`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
-   扩大转换必须存在于已分配的函数的返回类型的相反方向或`Sub`到委托的返回类型。 在以下示例中，每个已分配的 lambda 表达式的主体必须为数据类型扩大到`Integer`因为的返回类型`del1`是`Integer`。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 如果`Option Strict`设置为`Off`，则两个方向中删除了扩大限制。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>省略参数规范  
 放松要求的委托还允许你完全忽略中的分配方法的参数规范：  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 请注意，不能指定某些参数，并省略其他人。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 若要省略参数的功能非常有用的情况下，例如定义事件处理程序，其中涉及多个复杂的参数。 不使用一些事件处理程序的参数。 相反，处理程序直接访问的控件的事件注册时，并忽略这些参数的状态。 放松要求的委托，可省略不产生多义性时此类声明中的自变量。 在下面的示例中，完全指定的方法`OnClick`可以重写为`RelaxedOnClick`。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 示例  
 在前面的示例使用 lambda 表达式以便轻松查看类型关系。 但是，允许使用的委托分配相同松弛法`AddressOf`， `Handles`，或`AddHandler`。  
  
 在以下示例中，函数`f1`， `f2`， `f3`，和`f4`都可以分配到`Del1`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 下面的示例是仅当`Option Strict`设置为`Off`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>删除函数返回值  
 宽松的委托转换使您能够分配到函数`Sub`委托，有效地忽略该函数的返回值。 但是，不能分配`Sub`到函数委托。 在下面的示例中，函数的地址`doubler`分配给`Sub`委托`Del3`。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>请参阅

- [Lambda 表达式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [扩大转换和收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [委托](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [如何：将过程传递给 Visual Basic 中的另一个过程](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
