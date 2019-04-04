---
title: 使用反射 (Visual Basic) 访问特性
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e5cbce8529cc7554a8edacb2d83dabb73a495eec
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827637"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>使用反射 (Visual Basic) 访问特性
你可以定义自定义特性并将其放入源代码中这一事实，在没有检索该信息并对其进行操作的方法的情况下将没有任何价值。 通过使用反射，可以检索通过自定义特性定义的信息。 主要方法是 `GetCustomAttributes`，它返回对象数组，这些对象在运行时等效于源代码特性。 此方法有多个重载版本。 有关详细信息，请参阅 <xref:System.Attribute>。  
  
 特性规范，例如：  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 在概念上等效于此：  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 但是，在为特性查询 `SampleClass` 之前，代码将不会执行。 对 `SampleClass` 调用 `GetCustomAttributes` 会导致按上述方式构造并初始化一个 `Author` 对象。 如果该类具有其他特性，则将以类似方式构造其他特性对象。 然后 `GetCustomAttributes` 会以数组形式返回 `Author` 对象和任何其他特性对象。 之后你便可以循环访问此数组，根据每个数组元素的类型确定所应用的特性，并从特性对象中提取信息。  
  
## <a name="example"></a>示例  
 此处是一个完整的示例。 定义自定义特性、将其应用于多个实体，并通过反射对其进行检索。  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic 编程指南](../../../../visual-basic/programming-guide/index.md)
- [检索存储在特性中的信息](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [反射 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [创建自定义特性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
