---
title: 表达式递归调用包含属性“<propertyname>”
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: a758d05cca5ca71943b0ef08184aef5b2c457739
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836839"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>表达式递归调用包含属性\<属性名称 >
中的语句`Set`属性定义的过程将值存储到的属性的名称。  
  
 保存属性值的建议的方法是定义`Private`变量中的属性的容器并将其同时`Get`和`Set`过程。 `Set`过程应传入值存储在此`Private`变量。  
  
 `Get`过程的行为类似于`Function`过程中，因此它可以将值分配为属性名称并将控制权返回由遇到`End Get`语句。 但是，建议的方法是包括`Private`变量中的值作为[Return 语句](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Set`过程的行为类似于`Sub`过程，它将不会返回一个值。 因此，过程或属性名称已在没有特殊含义`Set`，也不能将值存储到其中。  
  
 下面的示例说明了可能会导致此错误消息，然后通过建议的方法的方法。  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参阅 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42026  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   重写属性定义要使用建议的方法，如在前面的示例所示。  
  
## <a name="see-also"></a>请参阅

- [属性过程](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set 语句](../../../visual-basic/language-reference/statements/set-statement.md)
