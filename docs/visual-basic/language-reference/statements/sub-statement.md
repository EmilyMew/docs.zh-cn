---
title: Sub 语句 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817222"
---
# <a name="sub-statement-visual-basic"></a>Sub 语句 (Visual Basic)
声明名称、 参数和定义的代码`Sub`过程。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>部件  
  
-   `attributelist`  
  
     可选。 请参阅[属性列表](attribute-list.md)。  
  
-   `Partial`  
  
     可选。 指示分部方法的定义。 请参阅[分部方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)。  
  
-   `accessmodifier`  
  
     可选。 可以是以下各项之一：  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `proceduremodifiers`  
  
     可选。 可以是以下各项之一：  
  
    -   [重载](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     可选。 请参阅[共享](../modifiers/shared.md)。  
  
-   `Shadows`  
  
     可选。 请参阅[Shadows](../modifiers/shadows.md)。  
  
-   `Async`  
  
     可选。 请参阅[异步](../modifiers/async.md)。  
  
-   `name`  
  
     必需。 该过程的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。 若要创建一个类的构造函数过程，请设置的名称`Sub`过程`New`关键字。 有关详细信息，请参阅[对象生存期：如何创建和销毁对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
-   `typeparamlist`  
  
     可选。 针对泛型过程的类型参数的列表。 请参阅[类型列表](type-list.md)。  
  
-   `parameterlist`  
  
     可选。 表示此过程的参数的本地变量名称的列表。 请参阅[参数列表](parameter-list.md)。  
  
-   `Implements`  
  
     可选。 指示此过程将实现一个或多个`Sub`过程，此过程包含类或结构实现接口中定义每个。 请参阅[实现语句](implements-statement.md)。  
  
-   `implementslist`  
  
     如果提供 `Implements`，则是必需的。 所实现的 `Sub` 过程的列表。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     每个 `implementedprocedure` 都具有以下语法和部件：  
  
     `interface.definedname`  
  
    |部件|描述|  
    |---|---|  
    |`interface`|必需。 此过程实现的接口的名称的包含类或结构。|  
    |`definedname`|必需。 在 `interface` 中用于定义过程的名称。|  
  
-   `Handles`  
  
     可选。 指示此过程可以处理一个或多个特定事件。 请参阅[处理](handles-clause.md)。  
  
-   `eventlist`  
  
     如果提供 `Handles`，则是必需的。 此过程处理的事件的列表。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     每个 `eventspecifier` 都具有以下语法和部件：  
  
     `eventvariable.event`  
  
    |部件|描述|  
    |---|---|  
    |`eventvariable`|必需。 声明的类或结构，它会引发事件的数据类型的对象变量。|  
    |`event`|必需。 此过程处理的事件的名称。|  
  
-   `statements`  
  
     可选。 要在此过程中运行的语句块。  
  
-   `End Sub`  
  
     终止此过程的定义。  
  
## <a name="remarks"></a>备注  
 在过程内必须是所有可执行代码。 使用`Sub`过程时不想要将值返回给调用代码。 使用`Function`过程时要返回的值。  
  
## <a name="defining-a-sub-procedure"></a>定义 Sub 过程  
 您可以定义`Sub`只能在模块级别的过程。 Sub 过程的声明上下文，因此，必须类、 结构、 模块或接口，且不能为源文件、 命名空间、 过程或块。 有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。  
  
 `Sub` 过程默认为公共访问。 可以使用访问修饰符来调整其访问级别。  
  
 如果过程使用`Implements`关键字、 包含类或结构必须具有`Implements`紧跟在后面的语句及其`Class`或`Structure`语句。 `Implements`语句必须包括在中指定每个接口`implementslist`。 但是，通过该接口定义的名称`Sub`(在`definedname`) 不需要此过程的名称匹配 (在`name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>返回从 Sub 过程  
 当`Sub`过程返回到调用代码时，继续执行调用了它的语句之后的语句。  
  
 下面的示例演示从返回`Sub`过程。  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub`并`Return`语句会导致立即退出`Sub`过程。 任意数量的`Exit Sub`并`Return`语句可以在过程中，任何位置出现，并且可以混合`Exit Sub`和`Return`语句。  
  
## <a name="calling-a-sub-procedure"></a>调用一个 Sub 过程  
 在调用`Sub`过程的方法是在语句中使用的过程名称，然后按照该名称与在括号中其自变量列表。 仅当不提供任何参数，可以省略括号。 但是，你的代码是始终使用圆括号更具可读性。  
  
 一个`Sub`过程和一个`Function`过程可以具有参数，并且执行一系列语句。 但是，`Function`过程返回一个值，以及一个`Sub`过程不会。 因此，不能使用`Sub`在表达式中的过程。  
  
 可以使用`Call`关键字调用时`Sub`大多数使用不推荐使用过程中，但是该关键字。 有关详细信息，请参阅[Call 语句](call-statement.md)。  
  
 Visual Basic 有时会重新排列算术表达式来提高内部工作效率。 出于此原因，如果在参数列表包含表达式调用其他过程，您不应假定，将按特定顺序调用这些表达式。  
  
## <a name="async-sub-procedures"></a>Async Sub 过程  
 通过使用异步功能，可以调用异步函数，而无需使用显式回调或手动拆分跨多个函数或 lambda 表达式的代码。  
  
 如果您将过程标记为与[异步](../modifiers/async.md)修饰符，可以使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)过程中的运算符。 当控件到达`Await`中的表达式`Async`过程中，控件返回到调用方，并在该过程的进度被挂起，直到等待的任务完成。 任务完成后，可以在该过程中恢复执行。  
  
> [!NOTE]
>  `Async`过程返回到调用方时遇到任一的第一个等待的对象不是完全或末尾`Async`达到过程，以先发生者为准。  
  
 此外可以将标记[Function 语句](function-statement.md)与`Async`修饰符。 `Async`函数可以具有的返回类型<xref:System.Threading.Tasks.Task%601>或<xref:System.Threading.Tasks.Task>。 示例更高版本在本主题演示`Async`函数的返回类型为<xref:System.Threading.Tasks.Task%601>。  
  
 `Async` `Sub` 过程主要用于事件处理程序的值不能返回。 `Async` `Sub`无法等待过程，和的调用方`Async``Sub`过程无法捕获的异常的`Sub`过程，则会引发。  
  
 `Async`过程不能声明任何[ByRef](../modifiers/byref.md)参数。  
  
 有关详细信息`Async`过程，请参阅[使用 Async 和 Await 的异步编程](../../../visual-basic/programming-guide/concepts/async/index.md)，[异步程序中的控制流](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)，并[异步返回类型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>示例  
 下面的示例使用`Sub`语句来定义名称、 参数和窗体的主体的代码`Sub`过程。  
  
 [!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]  
  
## <a name="example"></a>示例  
 在以下示例中，`DelayAsync`是`Async``Function`具有返回类型的<xref:System.Threading.Tasks.Task%601>。 `DelayAsync` 具有返回整数的 `Return` 语句。 因此，函数声明`DelayAsync`必须具有返回类型为`Task(Of Integer)`。 因为返回类型是`Task(Of Integer)`的评估`Await`中的表达式`DoSomethingAsync`如下语句所示得出整数： `Dim result As Integer = Await delayTask`。  
  
 `startButton_Click`过程是一种`Async Sub`过程。 因为`DoSomethingAsync`是`Async`函数，为调用任务`DoSomethingAsync`必须等待，如以下语句所示： `Await DoSomethingAsync()`。 `startButton_Click` `Sub`过程必须使用定义`Async`修饰符，因此`Await`表达式。  
  
 [!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [Implements 语句](implements-statement.md)
- [Function 语句](function-statement.md)
- [参数列表](parameter-list.md)
- [Dim 语句](dim-statement.md)
- [Call 语句](call-statement.md)
- [Of](of-clause.md)
- [参数数组](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [如何：使用泛型类](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [过程疑难解答](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [分部方法](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
