---
title: 创建自定义特性 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 90e8e9b9a3fa8e0b488f41d035b017d6113213b5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814349"
---
# <a name="creating-custom-attributes-visual-basic"></a>创建自定义特性 (Visual Basic)
可通过定义特性类创建自己的自定义特性，特性类是直接或间接派生自 <xref:System.Attribute> 的类，可快速轻松地识别元数据中的特性定义。 假设希望使用编写类型的程序员的姓名来标记该类型。 可能需要定义一个自定义 `Author` 特性类：  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 类名是该特性的名称，即 `Author`。 由于该类派生自 `System.Attribute`，因此它是一个自定义特性类。 构造函数的参数是自定义特性的位置参数。 在此示例中，`name` 是位置参数。 所有公共读写字段或属性都是命名参数。 在本例中，`version` 是唯一的命名参数。 请注意，使用 `AttributeUsage` 特性可使 `Author` 特性仅对类和 `Structure` 声明有效。  
  
 可按如下方式使用这一新特性：  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage` 有一个命名参数 `AllowMultiple`，通过此命名参数可一次或多次使用自定义特性。 下面的代码示例创建了一个多用特性。  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 在下面的代码示例中，某个类应用了同一类型的多个特性。  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  如果特性类包含属性，则该属性必须为读写属性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Reflection>
- [Visual Basic 编程指南](../../../../visual-basic/programming-guide/index.md)
- [编写自定义特性](../../../../standard/attributes/writing-custom-attributes.md)
- [反射 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [使用反射访问特性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
