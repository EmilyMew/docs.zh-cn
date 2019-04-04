---
title: 如何：编写扩展方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d6f8b85945bd400d1f4b54a50260d72c750add8b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819100"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>如何：编写扩展方法 (Visual Basic)
扩展方法，可将方法添加到现有类。 可以调用扩展方法，就像该类的实例。  
  
### <a name="to-define-an-extension-method"></a>若要定义的扩展方法  
  
1.  在 Visual Studio 中打开新的或现有 Visual Basic 应用程序。  
  
2.  在您要在其中定义扩展方法，该文件的顶部，包括以下 import 语句：  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  在新的或现有应用程序中的模块内, 开始使用扩展属性的方法定义：  
  
    ```  
    <Extension()>  
    ```  
  
4.  以普通方式声明你的方法，只不过的第一个参数的类型必须是你想要扩展的数据类型。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>示例  
 下面的示例声明模块中的扩展方法`StringExtensions`。 第二个模块， `Module1`，将导入`StringExtensions`和调用的方法。 扩展方法必须在范围内，被调用时。 扩展方法`PrintAndPunctuate`扩展了<xref:System.String>类显示的字符串实例的方法后, 跟标点符号中发送作为参数的字符串。  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 请注意，方法是使用两个参数定义，仅有一个调用。 第一个参数， `aString`，在方法中定义绑定到`example`，实例`String`调用的方法。 示例输出如下所示：  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [扩展方法](./extension-methods.md)
- [Module 语句](../../../../visual-basic/language-reference/statements/module-statement.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
