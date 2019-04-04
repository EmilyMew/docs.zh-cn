---
title: Visual Basic 中的 Main 过程
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833660"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic 中的 Main 过程
每个 Visual Basic 应用程序必须包含被调用的过程`Main`。 此过程可用作起始点并为应用程序的总体控制。 .NET Framework 调用你`Main`时它已加载你的应用程序并已准备好将控制传递给它的过程。 除非要创建 Windows 窗体应用程序，必须编写`Main`运行其自己的应用程序的过程。  
  
 `Main` 包含先运行的代码。 在`Main`，可以确定在程序启动时首先加载哪个窗体，找出在系统上是否已在运行应用程序的副本，为应用程序建立了一组变量或打开应用程序所需的数据库。  
  
## <a name="requirements-for-the-main-procedure"></a>主要过程的要求  
 在运行其自身 （通常使用扩展名为.exe) 文件必须包含`Main`过程。 （例如使用扩展名为.dll) 的库不会运行其自己并不需要`Main`过程。 您可以创建不同类型的项目的要求如下所示：  
  
-   控制台应用程序可以独立运行，并且必须提供至少一个`Main`过程。 .  
  
-   Windows 窗体应用程序上运行其自己。 但是，Visual Basic 编译器会自动生成`Main`过程在此类应用程序，并且您无需编写一个。  
  
-   不需要类库`Main`过程。 其中包括 Windows 控件库和 Web 控件库。 Web 应用程序部署为类库。  
  
## <a name="declaring-the-main-procedure"></a>声明的主要过程  
 有四种方法来声明`Main`过程。 它可以采用自变量和其可以或不返回值。  
  
> [!NOTE]
>  如果声明`Main`在类中，必须使用`Shared`关键字。 在模块中，`Main`不需要为`Shared`。  
  
-   最简单方法是声明`Sub`不采用自变量或返回值的过程。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` 此外可以返回`Integer`值，操作系统的退出代码为使用您的计划。 其他程序可以测试此代码通过检查 Windows ERRORLEVEL 值。 若要返回的退出代码，必须声明`Main`作为`Function`而不是过程`Sub`过程。  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main` 也可以采用`String`数组作为参数。 每个字符串数组中的包含一个用于调用程序的命令行参数。 您可以采取不同操作，具体取决于它们的值。  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   您可以声明`Main`来检查命令行参数而不是会返回退出代码，按如下所示。  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Visual Basic 程序的结构](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer 数据类型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String 数据类型](../../../visual-basic/language-reference/data-types/string-data-type.md)
