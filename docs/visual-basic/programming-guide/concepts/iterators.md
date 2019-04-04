---
title: 迭代器 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 313ce0c79a71af1b602ecd4ccc9bd0ebceb5696e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820826"
---
# <a name="iterators-visual-basic"></a>迭代器 (Visual Basic)
迭代器可用于逐步迭代集合，例如列表和数组。  
  
 迭代器方法或 `get` 访问器可对集合执行自定义迭代。 迭代器方法使用[产生](../../../visual-basic/language-reference/statements/yield-statement.md)语句返回每个元素，其中一个返回一次。 到达 `Yield` 语句时，会记住当前在代码中的位置。 下次调用迭代器函数时，将从该位置重新开始执行。  
  
 通过使用一个迭代器，从客户端代码[为每个...下一步](../../../visual-basic/language-reference/statements/for-each-next-statement.md)语句，或通过使用 LINQ 查询。  
  
 在以下示例中，`For Each` 循环的首次迭代导致 `SomeNumbers` 迭代器方法继续执行，直至到达第一个 `Yield` 语句。 此迭代返回的值为 3，并保留当前在迭代器方法中的位置。 在循环的下次迭代中，迭代器方法的执行将从其暂停的位置继续，直至到达 `Yield` 语句后才会停止。 此迭代返回的值为 5，并再次保留当前在迭代器方法中的位置。 到达迭代器方法的结尾时，循环便已完成。  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 迭代器方法或 `get` 访问器的返回类型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
 可以使用`Exit Function`或`Return`语句来终止迭代。  
  
 Visual Basic 迭代器函数或`get`访问器声明包含[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修饰符。  
  
 在 Visual Studio 2012 中 Visual Basic 中引入了迭代器。  
  
 **在本主题中**  
  
-   [简单迭代器](#BKMK_SimpleIterator)  
  
-   [创建集合类](#BKMK_CollectionClass)  
  
-   [Try 块](#BKMK_TryBlocks)  
  
-   [匿名方法](#BKMK_AnonymousMethods)  
  
-   [对泛型列表使用迭代器](#BKMK_GenericList)  
  
-   [语法信息](#BKMK_SyntaxInformation)  
  
-   [技术实现](#BKMK_Technical)  
  
-   [迭代器的使用](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  对于除简单迭代器示例主题中的所有示例，包括[导入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)语句`System.Collections`和`System.Collections.Generic`命名空间。  
  
## <a name="BKMK_SimpleIterator"></a>简单迭代器  
 下面的示例具有单个`Yield`内的语句[为...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。 在 `Main` 中，`For Each` 语句体的每次迭代都会创建一个对迭代器函数的调用，并将继续到下一个 `Yield` 语句。  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="BKMK_CollectionClass"></a>创建集合类  
 在以下示例中，`DaysOfTheWeek` 类实现 <xref:System.Collections.IEnumerable> 接口，此操作需要 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。 编译器隐式调用 `GetEnumerator` 方法，此方法返回 <xref:System.Collections.IEnumerator>。  
  
 `GetEnumerator`方法通过使用一次返回每个字符串之一`Yield`语句，和一个`Iterator`修饰符是函数声明中。  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 下例创建了一个包含动物集合的 `Zoo` 类。  
  
 引用类实例 (`theZoo`) 的 `For Each` 语句隐式调用 `GetEnumerator` 方法。 引用 `Birds` 和 `Mammals` 属性的 `For Each` 语句使用 `AnimalsForType` 命名迭代器方法。  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
## <a name="BKMK_TryBlocks"></a> Try 块  
 Visual Basic 允许`Yield`中的语句`Try`块[尝试...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 一个`Try`具有的块`Yield`语句可以有`Catch`阻止，并且可以具有`Finally`块。  
  
 下面的示例包括`Try`， `Catch`，和`Finally`迭代器函数中的块。 `Finally`迭代器函数中的块执行之前`For Each`迭代完成。  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 一个`Yield`语句不能包含在内`Catch`块或`Finally`块。  
  
 如果`For Each`正文 （而不是迭代器方法中） 引发异常，`Catch`未执行迭代器函数中的块，但`Finally`执行迭代器函数中的块。 一个`Catch`迭代器函数内的块将捕获在迭代器函数内部发生的异常。  
  
## <a name="BKMK_AnonymousMethods"></a> 匿名方法  
 在 Visual Basic 中的匿名函数可以是一个迭代器函数。 下面的示例阐释了这一点。  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 下面的示例有一个非迭代器方法，用于验证参数。 该方法返回一个匿名的迭代器，描述集合元素的结果。  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 如果验证改为在迭代器函数内部，不能开始的第一次迭代执行验证`For Each`正文。  
  
## <a name="BKMK_GenericList"></a>对泛型列表使用迭代器  
 在以下示例中，`Stack(Of T)` 泛型类实现 <xref:System.Collections.Generic.IEnumerable%601> 泛型接口。 `Push` 方法将值分配给类型为 `T` 的数组。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法通过使用 `Yield` 语句返回数组值。  
  
 除了泛型 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法，还必须实现非泛型 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。 这是因为从 <xref:System.Collections.IEnumerable> 继承了 <xref:System.Collections.Generic.IEnumerable%601>。 非泛型实现遵从泛型实现的规则。  
  
 本示例使用命名迭代器来支持通过各种方法循环访问同一数据集合。 这些命名迭代器为 `TopToBottom` 和 `BottomToTop` 属性，以及 `TopN` 方法。  
  
 `BottomToTop`属性声明包含`Iterator`关键字。  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
```  
  
## <a name="BKMK_SyntaxInformation"></a>语法信息  
 迭代器可用作一种方法，或一个 `get` 访问器。 不能在事件、实例构造函数、静态构造函数或静态析构函数中使用迭代器。  
  
 `Yield` 语句中必须存在从表达式类型到迭代器返回类型的隐式转换。  
  
 在 Visual Basic 中，迭代器方法不能含有任何`ByRef`参数。  
  
 在 Visual Basic 程序"Yield"不是保留的字并且仅当使用中时，它具有特殊含义`Iterator`方法或`get`访问器。  
  
## <a name="BKMK_Technical"></a>技术实现  
 即使将迭代器编写成方法，编译器也会将其转换为实际上是状态机的嵌套类。 只要客户端代码中的 `For Each...Next` 循环继续，此类就会跟踪迭代器的位置。  
  
 若要查看编译器执行的操作，可使用 Ildasm.exe 工具查看为迭代器方法生成的 Microsoft 中间语言代码。  
  
 当创建迭代器[类](../../../csharp/language-reference/keywords/class.md)或[结构](../../../csharp/language-reference/keywords/struct.md)，无需实现整个<xref:System.Collections.IEnumerator>接口。 编译器检测到迭代器时，会自动生成 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 接口的 `Current`、`MoveNext` 和 `Dispose` 方法。  
  
 在 `For Each…Next` 循环（或对 `IEnumerator.MoveNext` 的直接调用）的每次后续迭代中，下一个迭代器代码体都会在上一个 `Yield` 语句之后恢复。 然后继续下一个`Yield`语句，直至到达迭代器体的末尾，或直到`Exit Function`或`Return`遇到语句。  
  
 不支持迭代器<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>方法。 若要从头开始重新迭代，必须获取新的迭代器。  
  
 有关其他信息，请参阅[Visual Basic 语言规范](../../../visual-basic/reference/language-specification/index.md)。  
  
## <a name="BKMK_UseOfIterators"></a>迭代器的使用  
 需要使用复杂代码填充列表序列时，使用迭代器可保持 `For Each` 循环的简单性。 需执行以下操作时，这可能很有用：  
  
-   在第一次 `For Each` 循环迭代之后，修改列表序列。  
  
-   避免在 `For Each` 循环的第一次迭代之前完全加载大型列表。 一个示例是用于加载一批表格行的分页提取。 另一个示例关于 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，该方法在 .NET Framework 中实现迭代器。  
  
-   在迭代器中封装生成列表。 使用迭代器方法，可生成该列表，然后在循环中产出每个结果。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Yield 语句](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
