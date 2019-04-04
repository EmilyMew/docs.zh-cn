---
title: 如何：创建未签名的友元程序集 (Visual Basic)
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: 814c2584ea9e1e14c3af003a0515166f53b6d913
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819380"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>如何：创建未签名的友元程序集 (Visual Basic)
本示例演示如何将友元程序集和未签名的程序集一起使用。  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>创建程序集和友元程序集  
  
1.  打开命令提示。  
  
2.  创建一个名为 Visual Basic 文件`friend_signed_A.`，其中包含以下代码。 该代码使用 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性将 friend_signed_B 声明为友元程序集。  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  使用以下命令编译 friend_signed_A 并为其签名。  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  创建一个名为 Visual Basic 文件`friend_unsigned_B`，其中包含以下代码。 由于 friend_unsigned_A 将 friend_unsigned_B 指定为友元程序集，因此 friend_unsigned_B 中的代码可以访问 friend_unsigned_A 中的 `Friend` 类型和成员。  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  使用以下命令编译 friend_signed_B。  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     编译器生成的程序集的名称必须与传递给 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性的友元程序集的名称匹配。 通过使用可以显式设置程序集`/out`编译器选项。  
  
6.  运行 friend_signed_B.exe 文件。  
  
     程序将显示两个字符串：“Class1.Test”和“Class2.Test”。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性和 <xref:System.Security.Permissions.StrongNameIdentityPermission> 类之间具有相似之处。 主要区别是，<xref:System.Security.Permissions.StrongNameIdentityPermission> 可以要求安全权限来运行一段特定代码，而 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性控制 `Friend` 类型和成员的可见性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [.NET 中的程序集](../../../../standard/assembly/index.md)
- [友元程序集](../../../../standard/assembly/friend-assemblies.md)
- [如何：创建签名的友元程序集 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [编程指南概念](../../../../visual-basic/programming-guide/concepts/index.md)
