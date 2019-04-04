---
title: 对已声明元素的引用 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 5aea43c2dab4eb44ab40449ee6e970a28fdc4abb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821447"
---
# <a name="references-to-declared-elements-visual-basic"></a>对已声明元素的引用 (Visual Basic)
当你的代码引用已声明的元素时，Visual Basic 编译器匹配中该名称的相应声明您引用的名称。 如果多个元素具有相同名称声明，则可以控制哪些元素是由引用*合格*其名称。  
  
 编译器将尝试匹配对具有的名称声明的名称引用*最小范围*。 这意味着它启动，从而将该引用代码，并向外扩展到连续的元素的级别。  
  
 下面的示例演示对两个变量具有相同名称的引用。 此示例声明两个变量，每个命名`totalCount`，在模块中的作用域的不同级别`container`。 当该过程`showCount`将显示`totalCount`而无需限定，Visual Basic 编译器解析对具有最小范围，即内部的本地声明的声明引用`showCount`。 当有资格`totalCount`与包含模块`container`，则编译器将解析对范围更广的声明的引用。  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>符合条件的元素名称  
 如果你想要覆盖此搜索过程并指定一个名称，必须在范围更广中, 声明*限定*用范围更广的包含元素的名称。 在某些情况下，您可能还需要限定包含元素。  
  
 限定名称意味着要标识定义目标元素的位置的信息与在源语句中前面。 此信息称为*限定字符串*。 它可以包含一个或多个命名空间和模块，是类或结构。  
  
 模块、 类或结构，它包含目标元素，应明确指定的限定字符串。 容器又可能位于另一个包含元素，通常是命名空间中。 您可能需要限定字符串中包含多个包含元素。  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>若要通过限定其名称来访问已声明的元素  
  
1.  确定在其中定义元素的位置。 这可能包括一个命名空间或甚至命名空间的层次结构。 在最低级别命名空间，该元素必须包含在模块、 类或结构。  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  确定基于目标元素的位置的限定路径。 具有最高级别的命名空间中，转到最低级别的命名空间，开头和结尾模块、 类或结构，它包含目标元素。 在路径中的每个元素必须包含它后面的元素。  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  准备目标元素的限定字符串。 放置一个句点 (`.`) 的路径中每个元素之后。 你的应用程序必须具有对每个元素的访问限定字符串中。  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  编写表达式或赋值语句以正常方式引用目标元素。  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  在之前使用限定字符串的目标元素名称。 该名称应立即采用段 (`.`) 后面模块、 类或结构，它包含的元素。  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  编译器使用限定字符串来查找可与目标元素引用匹配的清晰、 明确声明。  
  
 您可能还需要限定名称引用，如果你的应用程序有权访问多个具有相同名称的编程元素。 例如，<xref:System.Windows.Forms>并<xref:System.Web.UI.WebControls>这两个命名空间包含具有`Label`类 (<xref:System.Windows.Forms.Label?displayProperty=nameWithType>和<xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>)。 如果你的应用程序使用这两个，或如果定义了自己`Label`类，则必须区分不同`Label`对象。 在变量声明中包括命名空间或导入别名。 下面的示例使用导入别名。  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>包含的其他元素的成员  
 当你使用另一个类或结构的非共享的成员时，必须首先限定成员名称的变量或表达式来指向类或结构的实例。 在以下示例中，`demoClass`是一个名为类的实例`class1`。  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 不能使用自身的类名来限定成员不是[共享](../../../../visual-basic/language-reference/modifiers/shared.md)。 中的对象变量必须先创建一个实例 (在这种情况下`demoClass`)，然后通过变量名称引用它。  
  
 如果类或结构具有`Shared`成员，可以限定该成员使用的类或结构的名称或变量或指向实例的表达式。  
  
 模块不具有任何单独的实例，且所有其成员`Shared`默认情况下。 因此，您有资格模块名称的模块成员。  
  
 下面的示例演示对模块成员过程的限定的引用。 此示例声明两个`Sub`过程，其名称`perform`，在项目中的不同模块中。 每个可以指定而无需限定在其自己的模块，但如果从其他位置引用必须是限定。 因为最后一个引用在`module3`不符合的条件`perform`，编译器无法解析该引用。  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>对项目的引用  
 若要使用[公共](../../../../visual-basic/language-reference/modifiers/public.md)另一个项目中定义的元素，则必须首先设置*引用*对该项目的程序集或类型库。 若要设置的引用，请单击**添加引用**上**项目**菜单中或使用[/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)命令行编译器选项。  
  
 例如，可以使用的 XML 对象模型[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 如果引用设置为<xref:System.Xml>命名空间中，您可以声明和使用的任何类，如<xref:System.Xml.XmlDocument>。 下面的示例使用<xref:System.Xml.XmlDocument>。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>导入包含元素  
 可以使用[Imports 语句 （.NET Namespace 和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)到*导入*包含的模块或你想要使用的类的命名空间。 这使您可以引用而没有完全限定其名称在导入的命名空间中定义的元素。 下面的示例将重写前面的示例，若要导入<xref:System.Xml>命名空间。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 此外，`Imports`语句可以定义*导入别名*为每个导入的命名空间。 这可以使较短且更易于读取的源代码。 下面的示例将重写前面的示例使用`xD`的别名作为<xref:System.Xml>命名空间。  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports`语句不会将其他项目中的元素提供给你的应用程序。 也就是说，它才会对引用的设置的位置。 只需导入命名空间不要求限定该命名空间中定义的名称。  
  
 此外可以使用`Imports`语句导入模块、 类、 结构和枚举。 然后可以使用此类导入的元素，而无需限定的成员。 但是，始终必须限定非共享的成员的类和结构的变量或表达式的计算结果为类或结构的实例。  
  
## <a name="naming-guidelines"></a>命名准则  
 如果定义了两个或多个具有相同名称的编程元素*名称多义性*时编译器将尝试解析对该名称的引用。 如果有多个一个定义位于范围内，或如果没有定义是在作用域中，则无法解析引用。 有关示例，请参阅此帮助页上的"限定引用示例"。  
  
 通过提供唯一的名称的所有元素，可以避免名称多义性。 然后您可以对进行引用的任何元素而无需限定其名称与命名空间、 模块或类。 您还可以减少意外引用错误的元素的可能性。  
  
## <a name="shadowing"></a>阴影操作  
 当两个编程元素共享相同的名称时，可以隐藏其中一个，或*卷影*，另一个。 隐藏的元素不是可用于引用;相反，当你的代码使用隐藏的元素名称时，Visual Basic 编译器将其解析为隐藏的元素。 有关示例的更多详细说明，请参阅[Visual Basic 中的隐藏](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## <a name="see-also"></a>请参阅

- [已声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [New 运算符](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
