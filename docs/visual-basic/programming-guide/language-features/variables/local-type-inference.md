---
title: 局部类型推理 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826816"
---
# <a name="local-type-inference-visual-basic"></a>局部类型推理 (Visual Basic)
使用 Visual Basic 编译器*类型推理*以确定未声明的局部变量的数据类型`As`子句。 编译器将推断变量的初始化表达式的类型的类型。 这使您无需显式声明一个类型，声明变量，如下面的示例中所示。 由于声明，而两者`num1`和`num2`强类型为整数。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  如果不希望`num2`在前面的示例以类型化为`Integer`，可以通过使用声明，例如指定另一种类型`Dim num3 As Object = 3`或`Dim num4 As Double = 3`。  

> [!NOTE]
>  类型推断可仅用于非静态局部变量;它不能用于确定类字段、 属性或函数的类型。
 
 局部类型推理在过程级别进行应用。 它不能用于声明在模块级别 （在类、 结构、 模块或接口，但不是在过程或块） 的变量。 如果`num2`上一示例中而不是一个过程中的本地变量类的字段，声明会导致出错`Option Strict`，并将对其分类`num2`作为`Object`与`Option Strict`关闭。 同样，局部类型推理不适用于过程级变量声明为`Static`。  
  
## <a name="type-inference-vs-late-binding"></a>类型推理与。后期绑定  
 使用类型推理的代码类似于依赖后期绑定代码。 但是，类型推断为强类型的变量而不是将其保留为`Object`。 编译器使用变量的初始值设定项来确定在编译时生成早期绑定代码变量的类型。 在上一示例中， `num2`，例如`num1`，类型化为`Integer`。  
  
 早期绑定的变量的行为不同于后期绑定变量，并仅在运行时知道它的类型。 尽早知道类型使编译器能够识别问题，然后执行、 准确地说，分配的内存和执行其他优化。 早期绑定还使 Visual Basic 的集成的开发环境 (IDE)，IntelliSense 将帮助提供有关对象的成员。 早期绑定也是首选的性能。 这是因为后期绑定变量中存储的所有数据都必须为类型都包装`Object`，并在运行时访问该类型的成员使程序运行较慢。  
  
## <a name="examples"></a>示例  
 未声明本地变量时，会发生类型推理`As`子句和初始化。 编译器使用已分配的初始值的类型作为变量的类型。 例如，以下代码行的每个声明类型的变量的`String`。  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 下面的代码演示两个等效方法来创建整数数组。  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 它可以方便地使用类型推理来确定循环控制变量的类型。 在下面的代码中，编译器推断`number`是`Integer`因为`someNumbers2`上一示例中是一个整数数组。  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 可以在使用局部类型推理`Using`语句，以建立资源名称的类型，如以下示例所示。  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 如以下示例所示，还可以从函数的返回值推断变量类型。 这两`pList1`并`pList2`是数组的进程，因为`Process.GetProcesses`返回进程的数组。  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` 允许指定特定文件中是否允许在局部类型推理。 若要启用或阻止该选项，请在文件的开头键入以下语句之一。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 如果未指定的值`Option Infer`在代码中，编译器默认设置是`Option Infer On`。 有关从升级项目[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]或更早版本，编译器默认`Option Infer Off`。  
  
 如果为文件中 `Option Infer` 设置的值与在 IDE 中或在命令行上设置的值冲突，则文件中的值优先。  
  
 有关详细信息，请参阅[Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)并[编译页，项目设计器 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>请参阅

- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [早期绑定和后期绑定](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next 语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 语句](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
