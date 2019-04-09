---
title: For Each...Next 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: 5081f80ad0da738ebb950bcd649af7a593582356
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824330"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next 语句 (Visual Basic)
集合中每个元素重复一组语句。  
  
## <a name="syntax"></a>语法  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`element`|在所需`For Each`语句。 在中为可选`Next`语句。 变量。 用于循环访问集合的元素。|  
|`datatype`|如果使用`element`不已声明。 数据类型的`element`。|  
|`group`|必需。 具有集合类型或对象的类型的变量。 表示的集合对其`statements`要重复。|  
|`statements`|可选。 一个或多个语句之间`For Each`并`Next`中每一项上运行的`group`。|  
|`Continue For`|可选。 将控制转移到开头`For Each`循环。|  
|`Exit For`|可选。 将控制的转移`For Each`循环。|  
|`Next`|必需。 终止的定义`For Each`循环。|  
  
## <a name="simple-example"></a>简单的示例  
 使用`For Each`...`Next`循环时想要为集合或数组的每个元素重复一组语句。  
  
> [!TIP]
>  一个[为...下一条语句](../../../visual-basic/language-reference/statements/for-next-statement.md)正常时，您可以将每次迭代的循环控制变量与相关联，并确定该变量的初始值和最终值。 但时处理的集合，初始和最终值的概念不是有意义，并且您不必知道集合中存在的元素数量。 在这种情况下， `For Each`...`Next`循环通常是更好的选择。  
  
 在以下示例中， `For Each`...`Next` 语句循环访问列表集合的所有元素。  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 有关更多示例，请参阅[集合](../../../standard/collections/index.md)并[数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="nested-loops"></a>嵌套的循环  
 可以嵌套`For Each`放置另一个循环内的循环。  
  
 下面的示例演示嵌套`For Each`...`Next` 结构。  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 当嵌套循环时，每个循环必须具有一个唯一`element`变量。  
  
 此外可以嵌套不同类型的控制结构彼此内。 有关详细信息，请参阅[嵌套控制结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>有关退出并继续  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)语句会导致执行退出`For`...`Next` 到后面的语句的循环，并将控制权`Next`语句。  
  
 `Continue For`语句控制将立即转移到循环的下一个迭代。 有关详细信息，请参阅[Continue 语句](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下面的示例演示如何使用`Continue For`和`Exit For`语句。  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 可以将任意数量的`Exit For`中的语句`For Each`循环。 当使用内嵌套`For Each`循环，`Exit For`会导致执行到下一个较高级别的嵌套退出最里面的循环，并将控制权。  
  
 `Exit For` 通常在某些条件的评估后使用，因为在`If`...`Then`...`Else`结构。 您可能想要使用`Exit For`满足以下条件：  
  
-   继续循环访问是不必要或不可能。 这可能引起错误的值或终止请求。  
  
-   在捕获到异常`Try`...`Catch`...`Finally`.可以使用`Exit For`末尾的`Finally`块。  
  
-   存在无限循环，这是一个循环，无法运行大型或甚至无限数量的次数。 如果检测到此类情况，可以使用`Exit For`来退出循环。 有关详细信息，请参阅[执行操作...循环语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="iterators"></a>Iterators  
 您使用*迭代器*若要对集合执行自定义迭代。 一个迭代器，可以是函数或`Get`访问器。 它使用`Yield`语句返回一次的集合的每个元素。  
  
 通过使用调用迭代器`For Each...Next`语句。 `For Each` 循环的每次迭代都会调用迭代器。 当`Yield`语句到达迭代器中的表达式中`Yield`语句会返回，并保留当前代码中的位置。 下次调用迭代器时，将从该位置重新开始执行。  
  
 以下示例使用迭代器函数。 迭代器函数具有`Yield`内的语句[为...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。 在中`ListEvenNumbers`方法中，每次迭代`For Each`语句体创建对迭代器函数，并将继续到下一步的调用`Yield`语句。  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 有关详细信息，请参阅[迭代器](../../programming-guide/concepts/iterators.md)， [Yield 语句](../../../visual-basic/language-reference/statements/yield-statement.md)，并[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
## <a name="technical-implementation"></a>技术实现  
 当`For Each`...`Next` 运行语句时，Visual Basic 将集合仅一次，在循环开始之前进行评估。 如果更改了语句块`element`或`group`，这些更改不会影响循环的迭代。  
  
 当集合中的所有元素已连续都分配给`element`，则`For Each`循环停止并将控制权传递到后面的语句`Next`语句。  
  
 如果`element`尚未被外部声明此循环中，必须将其声明中`For Each`语句。 您可以声明的类型`element`通过使用显式`As`语句，也可以依赖类型推断来分配类型。 在任一情况下，作用域的`element`是循环的正文。 但是，您無法宣告`element`外部和内部循环。  
  
 您可以选择指定`element`在`Next`语句。 这可提高应用程序的可读性，尤其是在具有嵌套`For Each`循环。 您必须指定相同的变量作为所显示的相应`For Each`语句。  
  
 你可能想要避免更改的值`element`在循环内。 执行此操作可以导致更难以阅读和调试代码。 值更改`group`不会影响集合或它的元素，当首次进入循环时确定。  
  
 当要嵌套循环，如果`Next`外部的嵌套级别的语句之前遇到`Next`的内部级别，编译器会引发错误。 但是，编译器可检测到这只有在指定重叠错误`element`中每个`Next`语句。  
  
 如果你的代码依赖于遍历集合中特定的顺序， `For Each`...`Next`循环不是最佳选择，除非您知道的枚举器对象的特征，否则该集合公开。 遍历的顺序不由 Visual Basic 中，而是由确定<xref:System.Collections.IEnumerator.MoveNext%2A>枚举器对象的方法。 因此，您可能无法预测哪个元素集合中返回的第一个`element`，或者其中的下一个要返回给定元素之后。 您可能会获得更可靠的结果使用不同的循环结构类似于`For`...`Next`或`Do`...`Loop`.  
  
 数据类型`element`这样的数据类型的元素必须是`group`可以转换为它。  
  
 数据类型的`group`必须是指集合或数组，它是可枚举的引用类型。 通常这意味着`group`实现的对象是指<xref:System.Collections.IEnumerable>界面`System.Collections`命名空间或<xref:System.Collections.Generic.IEnumerable%601>接口的`System.Collections.Generic`命名空间。 `System.Collections.IEnumerable` 定义<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法，返回集合的枚举器对象。 枚举器对象实现`System.Collections.IEnumerator`界面`System.Collections`命名空间，并公开<xref:System.Collections.IEnumerator.Current%2A>属性和<xref:System.Collections.IEnumerator.Reset%2A>和<xref:System.Collections.IEnumerator.MoveNext%2A>方法。 Visual Basic 使用这些来遍历集合。  
  
### <a name="narrowing-conversions"></a>收缩转换  
 当`Option Strict`设置为`On`，收缩转换通常会导致编译器错误。 在`For Each`语句，但是，从中的元素的转换`group`到`element`进行计算并在运行时，执行和禁止编译器错误引起的收缩转换。  
  
 在下面的示例中，分配`m`作为初始值`n`无法进行编译时`Option Strict`已启用，因为转换`Long`到`Integer`是收缩转换。 在中`For Each`语句，但是，编译器错误，是报告，即使对分配`number`需要从同一个转换`Long`到`Integer`。 在`For Each`语句中有很多，运行时错误发生时<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>应用于很多。  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>IEnumerator 调用  
 当执行`For Each`...`Next`循环启动时，Visual Basic 验证`group`引用有效的集合对象。 如果没有，则引发异常。 否则，它会调用<xref:System.Collections.IEnumerator.MoveNext%2A>方法和<xref:System.Collections.IEnumerator.Current%2A>要返回的第一个元素的枚举器对象的属性。 如果`MoveNext`指示已没有下一个元素，即，如果集合为空，`For Each`循环停止并将控制权传递到后面的语句`Next`语句。 否则，Visual Basic 设置`element`到第一个元素和运行的语句块。  
  
 每次 Visual Basic 遇到`Next`语句，它返回到`For Each`语句。 它将再次调用`MoveNext`和`Current`要返回的下一个元素，并再次运行块或停止根据结果的循环。 此过程将继续，直至`MoveNext`指示不存在下一个元素或`Exit For`遇到语句。  
  
 **对集合进行修改。** 返回的枚举器对象<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常不允许您通过添加、 删除、 替换或重新排序的任何元素更改的集合。 如果您已经启动后更改的集合， `For Each`...`Next`循环枚举器对象将变为无效，和下一步尝试访问的元素将导致<xref:System.InvalidOperationException>异常。  
  
 但是，修改此阻止不取决于 Visual Basic，而是由实现<xref:System.Collections.IEnumerable>接口。 可以实现`IEnumerable`允许在迭代期间修改的方式。 如果你正在考虑进行这种动态修改，请确保您了解的特征`IEnumerable`实现上使用的集合。  
  
 **修改集合元素。** <xref:System.Collections.IEnumerator.Current%2A>枚举器对象的属性是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，并返回每个集合元素的本地副本。 这意味着您不能修改这些元素本身中`For Each`...`Next`循环。 进行任何修改会影响仅从本地复制`Current`而不反映回基础集合。 但是，如果元素为引用类型，您可以修改它所指向的实例的成员。 下面的示例修改`BackColor`的每个成员`thisControl`元素。 但是，不能修改`thisControl`本身。  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 前面的示例可以修改`BackColor`的每个成员`thisControl`元素，但是不能修改`thisControl`本身。  
  
 **通过遍历数组。** 因为<xref:System.Array>类实现<xref:System.Collections.IEnumerable>接口，所有数组都公开<xref:System.Array.GetEnumerator%2A>方法。 这意味着可以循环访问数组`For Each`...`Next`循环。 但是，你只能读取数组元素。 你不能更改它们。  
  
## <a name="example"></a>示例  
 下面的示例通过使用列出的 C:\ 目录中的所有文件夹<xref:System.IO.DirectoryInfo>类。  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>示例  
 以下示例阐释了对集合排序的过程。 该示例的实例进行排序`Car`存储中的类<xref:System.Collections.Generic.List%601>。 `Car` 类实现 <xref:System.IComparable%601> 接口，此操作需要实现 <xref:System.IComparable%601.CompareTo%2A> 方法。  
  
 每次调用<xref:System.IComparable%601.CompareTo%2A>方法可用于排序的单一比较。 `CompareTo` 方法中用户编写的代码针对当前对象与另一个对象的每个比较返回一个值。 如果当前对象小于另一个对象，则返回的值小于零；如果当前对象大于另一个对象，则返回的值大于零；如果当前对象等于另一个对象，则返回的值等于零。 这使你可以在代码中定义大于、小于和等于条件。  
  
 在 `ListCars` 方法中，`cars.Sort()` 语句对列表进行排序。 对 <xref:System.Collections.Generic.List%601> 的 <xref:System.Collections.Generic.List%601.Sort%2A> 方法的此调用将导致为 `List` 中的 `Car` 对象自动调用 `CompareTo` 方法。  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>请参阅

- [集合](../../../standard/collections/index.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [循环结构](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [对象初始值设定项：命名和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [集合初始值设定项](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
