---
title: 扩展方法 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: aca8f18c4bc53318792a119617b1ca0d6c4cc32e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822071"
---
# <a name="extension-methods-visual-basic"></a>扩展方法 (Visual Basic)
扩展方法使开发人员能够将自定义功能添加到已定义而无需创建新的派生的类型的数据类型。 扩展方法使其可以编写可以像调用现有类型的实例方法那样调用的方法。  
  
## <a name="remarks"></a>备注  
 扩展方法只能`Sub`过程或`Function`过程。 不能定义扩展属性、 字段或事件。 必须使用扩展属性标记所有扩展方法`<Extension()>`从<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空间。  
  
 扩展方法定义中的第一个参数指定该方法所扩展的数据类型。 运行方法时，第一个参数是绑定到调用方法的数据类型的实例。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例定义`Print`扩展<xref:System.String>数据类型。 该方法使用`Console.WriteLine`显示字符串。 参数`Print`方法， `aString`，确保方法扩展<xref:System.String>类。  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 请注意，扩展方法定义用扩展特性标记`<Extension()>`。 将标记在其中定义该方法的模块是可选的但必须标记每个扩展方法。 <xref:System.Runtime.CompilerServices> 必须导入才能访问扩展属性。  
  
 扩展方法可以声明只能在模块中。 通常情况下，在其中定义扩展方法的模块不调用它的一个相同的模块。 相反，包含扩展方法是导入的模块，如果它必须是以使其进入作用域。 包含该模块后`Print`是在作用域，就像普通实例方法，如不采用任何参数，可以调用该方法`ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 下一步的示例中， `PrintAndPunctuate`，也是一个扩展<xref:System.String>，这次使用两个参数定义。 第一个参数， `aString`，确保扩展方法扩展<xref:System.String>。 第二个参数， `punc`，它要用作标点符号的字符串，它在作为参数传递时调用的方法。 该方法显示跟标点符号的字符串。  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 该方法调用中的字符串参数发送`punc`: `example.PrintAndPunctuate(".")`  
  
 下面的示例演示`Print`和`PrintAndPunctuate`定义和调用。 <xref:System.Runtime.CompilerServices> 将以导入定义模块以启用扩展属性的访问权限。  
  
### <a name="code"></a>代码  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 接下来，扩展方法引入作用域，名为。  
  
```vb  
Imports ConsoleApplication2.StringExtensions  
Module Module1  
  
    Sub Main()  
  
        Dim example As String = "Example string"  
        example.Print()  
  
        example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>注释  
 所有所需能够运行这些或类似的扩展方法是，它们是在作用域中。 如果包含扩展方法的模块在作用域，它在 IntelliSense 中可见，并可以像调用普通实例方法那样调用。  
  
 请注意，调用方法时, 未发送任何参数第一个参数。 参数`aString`前一种方法中定义绑定到`example`，实例`String`调用它们。 编译器将使用`example`作为参数发送到第一个参数。  
  
 如果设置为某个对象调用扩展方法`Nothing`，执行该扩展方法。 这不适用于普通实例方法。 您可以显式检查`Nothing`扩展方法中。  
  
## <a name="types-that-can-be-extended"></a>可以扩展的类型  
 您可以定义可以出现在 Visual Basic 参数列表，其中包括的大多数类型的扩展方法：  
  
-   类 （引用类型）  
  
-   结构 （值类型）  
  
-   接口  
  
-   委托  
  
-   ByRef 和 ByVal 参数  
  
-   泛型方法参数  
  
-   数组  
  
 第一个参数指定的数据类型的扩展方法扩展，因为它是必需的且不能为可选。 因此，`Optional`参数和`ParamArray`参数不能是参数列表中的第一个参数。  
  
 在后期绑定中不考虑扩展方法。 在下面的示例中，该语句`anObject.PrintMe()`将引发<xref:System.MissingMemberException>异常，相同的异常时将看到第二个`PrintMe`扩展方法定义已删除。  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a>最佳做法  
 扩展方法提供一种方便功能强大的方式来扩展现有类型。 但是，若要成功使用，还是有要考虑的一些要点。 这些注意事项主要适用于作者的类库，但它们可能会影响任何使用扩展方法的应用程序。  
  
 大多数情况下，您将添加到不属于您的类型的扩展方法是添加到您控制的类型的扩展方法相比更易受到攻击。 许多因素可能不属于您的类中可能会干扰你的扩展方法。  
  
-   如果存在任何可访问的实例成员具有与需要从实参向参数没有收缩转换与调用语句中的参数兼容的签名，将优先于任何扩展方法使用实例方法。 因此，如果相应的实例方法添加到类在某些时候，你依赖的现有扩展成员变得不可访问。  
  
-   扩展方法作者无法阻止其他程序员编写可能优先于原来的扩展名的冲突扩展方法。  
  
-   可以通过将扩展方法放置在自己的命名空间中来提高可靠性。 你的库的使用者可以包含的命名空间或排除它，或选择多个命名空间，独立于库的其余部分。  
  
-   它可能是更为安全的做法比扩展类，尤其是如果您不拥有该接口或类扩展接口。 在接口中的更改会影响每个类来实现它。 因此，作者可能不太可能要添加或更改在接口中的方法。 但是，如果一个类实现两个具有相同签名的扩展方法的接口，扩展方法都不可见。  
  
-   扩展可以最具体的类型。 在类型的层次结构，如果您选择从其派生许多其他类型，类型有可能将引入实例方法或其他可能会影响您的扩展方法的层。  
  
## <a name="extension-methods-instance-methods-and-properties"></a>扩展方法、 实例方法和属性  
 当范围内实例方法具有与调用语句的实参兼容的签名时，将任何扩展方法优先选择的实例方法。 实例方法具有优先权，即使扩展方法是更好的匹配项。 在以下示例中，`ExampleClass`包含名为的实例方法`ExampleMethod`它具有一个参数类型的`Integer`。 扩展方法`ExampleMethod`扩展`ExampleClass`，并具有一个类型参数`Long`。  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 首次调用`ExampleMethod`下面的代码中调用扩展方法，因为`arg1`是`Long`并且仅与兼容`Long`扩展方法中的参数。 第二次调用`ExampleMethod`已`Integer`自变量， `arg2`，它将调用实例方法。  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 现在反转这两种方法中的参数的数据类型：  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 这一次中的代码`Main`两次都调用实例方法。 这是因为两者`arg1`并`arg2`有扩大转换为`Long`，和实例方法优先于这两种情况中的扩展方法。  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 因此，扩展方法不能替换现有的实例方法。 但是，如果扩展方法具有相同的名称作为实例方法，但签名不冲突，则可以访问这两种方法。 例如，如果类`ExampleClass`包含一个名为方法`ExampleMethod`不采用任何参数，具有相同名称的扩展方法，但允许不同的签名，如下面的代码中所示。  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 此代码的输出如下所示：  
  
 `Extension method`  
  
 `Instance method`  
  
 这种情况是使用属性更简单： 如果扩展方法具有与它所扩展的类的属性相同的名称，该扩展方法不可见，且无法访问。  
  
## <a name="extension-method-precedence"></a>扩展方法优先级  
 作用域中并且可以访问两个具有相同签名的扩展方法时，将调用具有较高的优先级。 扩展方法的优先级基于用于将方法引入作用域的机制。 以下列表显示了优先级层次结构中的，从最高到最低。  
  
1.  在当前模块内定义的扩展方法。  
  
2.  扩展方法内定义数据类型在当前命名空间或其任何一个其父项，其中子命名空间具有更高的优先级比父命名空间。  
  
3.  当前文件中的任何类型导入内定义的扩展方法。  
  
4.  当前文件中任何命名空间导入内定义的扩展方法。  
  
5.  任何项目级类型导入内定义的扩展方法。  
  
6.  任何项目级命名空间导入内定义的扩展方法。  
  
 如果优先级不能解决多义性问题，可以使用完全限定的名称来指定要调用的方法。 如果`Print`前面的示例中的方法定义一个名为模块中`StringExtensions`，完全限定的名是`StringExtensions.Print(example)`而不是`example.Print()`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [扩展方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module 语句](../../../../visual-basic/language-reference/statements/module-statement.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [可选参数](./optional-parameters.md)
- [参数数组](./parameter-arrays.md)
- [属性概述](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
