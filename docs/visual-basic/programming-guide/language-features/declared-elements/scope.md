---
title: Visual Basic 中的范围
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 6139af65958cefe43578f436204fa6836a71de0b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823540"
---
# <a name="scope-in-visual-basic"></a>Visual Basic 中的范围
*作用域*声明的元素是一组的所有代码都可以引用它而无需限定其名称或使其可通过[Imports 语句 （.NET Namespace 和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。 元素可以具有以下级别之一的作用域：  
  
|级别|描述|  
|-----------|-----------------|  
|块范围|在声明它仅在代码中的可用块|  
|过程范围|适用于在其中声明的过程中的所有代码|  
|模块范围内|适用于在模块、 类或结构声明它的所有代码|  
|Namespace 作用域|适用于在其中声明的命名空间中的所有代码|  
  
 这些级别范围从最小 （块） 到最宽 （命名空间），其中*最小范围*意味着可以引用而无需限定的元素的代码的最小集。 有关详细信息，请参阅此页上的"级别的作用域"。  
  
## <a name="specifying-scope-and-defining-variables"></a>指定作用域，以及定义变量  
 在声明它时指定元素的范围。 作用域取决于以下因素：  
  
-   在其中声明该元素的区域 （块、 过程、 模块、 类或结构）  
  
-   包含元素的声明的命名空间  
  
-   为元素声明的访问级别  
  
 时要格外小心定义变量具有相同名称但不同的作用域，因为这样做可能会导致意外结果。 有关详细信息，请参阅 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="levels-of-scope"></a>级别的作用域  
 编程元素是在整个声明它的区域中可用。 同一区域中的所有代码可以无需限定其名称都引用该元素。  
  
### <a name="block-scope"></a>块范围  
 块是一组语句包含在启动和终止声明语句，如下所示：  
  
-   `Do` 和 `Loop`  
  
-   `For` [`Each`] 和 `Next`  
  
-   `If` 和 `End If`  
  
-   `Select` 和 `End Select`  
  
-   `SyncLock` 和 `End SyncLock`  
  
-   `Try` 和 `End Try`  
  
-   `While` 和 `End While`  
  
-   `With` 和 `End With`  
  
 如果您声明一个块内的变量，可以仅在该块中使用它。 在下面的示例中，整数变量的作用域`cube`是块之间`If`和`End If`，你可以不再引用`cube`时将执行传递到块之外。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  即使变量的作用域仅限于一个块，其生存期内仍为整个过程。 如果在该过程一次输入块，每个块变量将保留以前的值。 若要避免这种情况中的意外的结果，明智的做法是在块的开始处的块变量进行初始化。  
  
### <a name="procedure-scope"></a>过程范围  
 一个过程中声明的元素不在该过程外可用。 仅包含声明的过程可以使用它。 在此级别的变量是也称为*局部变量*。 将它们与声明[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)用或者不用[静态](../../../../visual-basic/language-reference/modifiers/static.md)关键字。  
  
 过程和块范围关系十分紧密。 如果要声明的变量在过程内，但在该过程中的任何块外，您可以将变量作为具有块范围，其中块就是整个过程。  
  
> [!NOTE]
>  所有局部元素，即使它们是`Static`变量，是专用于其显示的过程。 不能声明任何元素使用[公共](../../../../visual-basic/language-reference/modifiers/public.md)过程中的关键字。  
  
### <a name="module-scope"></a>模块范围内  
 为方便起见，单个字词*模块级别*同样适用于模块、 类和结构。 可以通过将声明语句之外的任何过程或块，但模块、 类或结构中声明此级别的元素。  
  
 在模块级别声明时，你选择的访问权限级别确定作用域。 包含模块、 类或结构的命名空间还会影响作用域。  
  
 为其声明的元素[专用](../../../../visual-basic/language-reference/modifiers/private.md)访问级别都可用的另一个模块中的任何代码的每个过程在该模块中，而不可用。 `Dim`语句在模块级别的默认值为`Private`如果不使用任何访问级别关键字。 但是，您使用可以进行的作用域和访问级别更明显`Private`中的关键字`Dim`语句。  
  
 模块中定义的所有过程的字符串变量，在以下示例中，可以都引用`strMsg`。 当调用第二个过程时，它将显示的字符串变量的内容`strMsg`对话框框中。  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace 作用域  
 如果声明在模块级别使用的元素[友元](../../../../visual-basic/language-reference/modifiers/friend.md)或[公共](../../../../visual-basic/language-reference/modifiers/public.md)关键字，将其提供给整个在其中声明该元素的命名空间的所有过程。 与前面的示例中，字符串变量进行如下更改`strMsg`可以由其声明的命名空间中的任意位置的代码引用。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace 作用域包括嵌套的命名空间。 可从命名空间内的元素也是可从嵌套在该命名空间内的任何命名空间。  
  
 如果你的项目不包含任何[Namespace 语句](../../../../visual-basic/language-reference/statements/namespace-statement.md)s，项目中的所有内容都是相同的命名空间中。 在这种情况下，可以将命名空间范围视为项目范围。 `Public` 模块、 类或结构中的元素也是可用于引用其项目的任何项目。  
  
## <a name="choice-of-scope"></a>所选的作用域  
 在声明变量时，您应记住以下几点选择其作用域内时。  
  
### <a name="advantages-of-local-variables"></a>本地变量的优点  
 本地变量是出于以下原因适合用于临时计算的任何类型：  
  
-   **避免名称冲突。** 本地变量名称不容易发生冲突。 例如，可以创建多个不同的过程包含一个名为变量`intTemp`。 只要每个`intTemp`被声明为局部变量，每个过程识别其自己的版本的`intTemp`。 任何一个步骤可能会更改其本地中的值`intTemp`而不会影响`intTemp`其他过程中的变量。  
  
-   **内存占用情况。** 本地变量仅在其过程运行时占用的内存。 该过程返回到调用代码时，会释放其内存。 与此相反，[共享](../../../../visual-basic/language-reference/modifiers/shared.md)并[静态](../../../../visual-basic/language-reference/modifiers/static.md)变量消耗内存资源，直到你的应用程序停止运行，因此，它们仅在必要时使用。 *实例变量*占用内存实例继续存在，这使它们更少比本地变量有效，但可能会比效率更高`Shared`或`Static`变量。  
  
### <a name="minimizing-scope"></a>最大程度减少作用域  
 一般情况下，当声明的任何变量或常量时，它编程最佳做法是使其范围尽可能窄 （块范围是最小）。 这有助于节约内存和最大程度减少你错误地引用错误的变量的代码的可能性。 同样，应将变量声明[静态](../../../../visual-basic/language-reference/modifiers/static.md)仅当有必要过程调用之间保留值。  
  
## <a name="see-also"></a>请参阅

- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [如何：控制变量的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [在 Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
