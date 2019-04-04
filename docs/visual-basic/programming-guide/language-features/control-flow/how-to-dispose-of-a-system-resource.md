---
title: 如何：释放系统资源 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: 2a399b92c66c8a88d10d661ff41aef58a82bbc2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829910"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>如何：释放系统资源 (Visual Basic)
可以使用`Using`块来确保系统在你的代码退出块时释放资源。 这是很有用，如果使用的这样做会消耗大量内存，或其他组件也想要使用的系统资源。  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>若要释放数据库连接时用完您的代码  
  
1.  请务必加入相应[Imports 语句 （.NET Namespace 和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)开头的源文件的数据库连接 (在这种情况下， <xref:System.Data.SqlClient>)。  
  
2.  创建`Using`块`Using`和`End Using`语句。 在块中，将处理与数据库连接的代码。  
  
3.  声明连接并创建它的一个实例作为的一部分`Using`语句。  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     不管您如何退出块，包括大小写的未经处理的异常的资源，系统都会释放。  
  
     请注意，不能访问`sqc`从外部`Using`阻止，因为其作用域被限制为块。  
  
     对系统资源，例如文件句柄或 COM 包装器，可以使用此相同的技术。 您使用`Using`当你以确保想要保留的资源可供其他组件后您退出时，阻止`Using`块。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.SqlClient.SqlConnection>
- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [决策结构](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [嵌套的控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using 语句](../../../../visual-basic/language-reference/statements/using-statement.md)
