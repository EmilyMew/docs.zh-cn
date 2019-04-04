---
title: Lambda 表达式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c43739e098a91d54d300fa7074d1563da179c0e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832107"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda 表达式 (Visual Basic)
一个*lambda 表达式*是函数或子例程没有可用于任何委托是有效的名称。 Lambda 表达式可以是函数或子例程，并且可以是单行或多行。 可以将值从当前作用域传递到 lambda 表达式中。  
  
> [!NOTE]
>  `RemoveHandler`语句是一个例外。 不能将传递的委托参数的 lambda 表达式中`RemoveHandler`。  
  
 使用创建 lambda 表达式`Function`或`Sub`关键字，就像创建标准函数或子例程。 但是，lambda 表达式包含在一个语句。  
  
 下面的示例是递增其参数和返回值的 lambda 表达式。 该示例显示了函数的这两个单行和多行 lambda 表达式语法。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 下面的示例是向控制台写入值的 lambda 表达式。 该示例显示了一个子例程的这两个单行和多行 lambda 表达式语法。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 请注意，在前面的示例中的 lambda 表达式将分配给变量的名称。 引用的变量，每当您调用 lambda 表达式。 您可以声明和调用 lambda 表达式在相同时，如下面的示例中所示。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Lambda 表达式可以返回作为函数调用的值 (如示例中所示[上下文](#context)本主题后面的部分)，或作为参数传递给参数接受一个委托类型，如以下所示示例。  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Lambda 表达式语法  
 Lambda 表达式的语法类似于标准函数或子例程。 差异如下所示：  
  
-   Lambda 表达式没有名称。  
  
-   Lambda 表达式不能有修饰符，如`Overloads`或`Overrides`。  
  
-   单行 lambda 函数不使用`As`子句指定返回类型。 相反，从 lambda 表达式的主体的计算结果为的值推断类型。 例如，如果 lambda 表达式的正文`cust.City = "London"`，其返回类型是`Boolean`。  
  
-   在多行 lambda 函数中，您也可以指定返回类型通过使用`As`子句，或忽略`As`子句，以便推断返回类型。 当`As`子句省略对于多行 lambda 函数、 返回类型被推断为从所有的基准类型`Return`中多行 lambda 函数的语句。 *基准类型*是所有其他类型可以扩大到的唯一类型。 如果无法确定此唯一类型，基准类型是数组中的所有其他类型可以缩小到的唯一类型。 如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。 在这种情况下，如果`Option Strict`设置为`On`，会发生编译器错误。  
  
     例如，如果表达式提供给`Return`语句包含类型的值`Integer`， `Long`，和`Double`，生成的数组类型是`Double`。 这两`Integer`并`Long`扩大到`Double`和仅`Double`。 因此， `Double` 是基准类型。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
-   单行函数的主体必须是返回一个值，而不是语句表达式。 没有任何`Return`单行函数的语句。 单行函数返回的值是表达式的函数的正文中的值。  
  
-   单行子例程的主体必须是单行语句。  
  
-   不包括的单行函数和子例程`End Function`或`End Sub`语句。  
  
-   可以通过使用指定的 lambda 表达式参数的数据类型`As`关键字或该参数的数据类型可以推断出。 必须必须推断数据类型或全部指定或者所有参数。  
  
-   `Optional` 和`Paramarray`不允许使用参数。  
  
-   不允许使用泛型参数。  
  
## <a name="async-lambdas"></a>异步 lambda  
 您可以轻松创建的包含异步处理通过使用 lambda 表达式和语句[异步](../../../../visual-basic/language-reference/modifiers/async.md)并[Await 运算符](../../../../visual-basic/language-reference/operators/await-operator.md)关键字。 例如，下面的 Windows 窗体示例包含一个调用和等待异步方法 `ExampleMethodAsync`的事件处理程序。  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 可以通过使用在异步 lambda 添加同一事件处理程序[AddHandler 语句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)。 若要添加此处理程序，请在 lambda 参数列表前添加一个 `Async` 修饰符，如下例所示。  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 有关如何创建和使用异步方法的详细信息，请参阅[使用 Async 和 Await 的异步编程](../../../../visual-basic/programming-guide/concepts/async/index.md)。  
  
## <a name="context"></a> 上下文  
 Lambda 表达式与在其中定义它的作用域共享其上下文。 它具有与包含作用域中编写任何代码的相同访问权限。 这包括访问成员变量、 函数和子例程， `Me`，包含作用域中的局部变量和参数。  
  
 访问本地变量和参数中包含的作用域可以扩展该作用域生存期。 只要引用 lambda 表达式的委托不能进行垃圾回收，会保留在原始环境变量的访问权限。 在以下示例中，变量`target`本地`makeTheGame`，在其中的方法的 lambda 表达式`playTheGame`定义。 请注意，返回的 lambda 表达式中，分配给`takeAGuess`中`Main`，仍有权访问本地变量`target`。  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 下面的示例演示了广泛的嵌套的 lambda 表达式的访问权限。 从执行返回的 lambda 表达式时`Main`作为`aDel`，它将访问这些元素：  
  
-   在其中定义类的字段： `aField`  
  
-   在其中定义类的一个属性： `aProp`  
  
-   方法的参数`functionWithNestedLambda`，在其中定义： `level1`  
  
-   局部变量的`functionWithNestedLambda`: `localVar`  
  
-   在其中嵌套 lambda 表达式的参数： `level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>将转换为委托类型  
 Lambda 表达式可以隐式转换为兼容的委托类型。 有关兼容性的一般要求的信息，请参阅[宽松委托转换](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。 例如，下面的代码示例显示了 lambda 表达式隐式转换为`Func(Of Integer, Boolean)`或匹配的委托签名。  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 下面的代码示例显示了 lambda 表达式隐式转换为`Sub(Of Double, String, Double)`或匹配的委托签名。  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 当您将 lambda 表达式分配给委托，或将它们作为参数传递给过程时，可以指定参数名称，但省略其数据类型，以便从委托中获取的类型。  
  
## <a name="examples"></a>示例  
  
-   下面的示例定义返回的 lambda 表达式`True`如果可以为 null 的参数分配的值，并`False`如果其值为`Nothing`。  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
-   下面的示例定义返回数组中的最后一个元素索引的 lambda 表达式。  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>请参阅

- [过程](./index.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [委托](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function 语句](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [可以为 null 的值类型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [如何：将过程传递给 Visual Basic 中的另一个过程](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [如何：创建一个 Lambda 表达式](./how-to-create-a-lambda-expression.md)
- [宽松委托转换](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
