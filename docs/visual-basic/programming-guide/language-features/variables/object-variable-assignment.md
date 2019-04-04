---
title: 对象变量赋值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: dff1b9bb9e87f827663786cac3f33531db41b2c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840271"
---
# <a name="object-variable-assignment-visual-basic"></a>对象变量赋值 (Visual Basic)
使用普通赋值语句将对象分配给对象变量。 可以分配对象表达式或[Nothing](../../../../visual-basic/language-reference/nothing.md)关键字，如下面的示例说明了。  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` 意味着没有当前分配给变量对象。  
  
## <a name="initialization"></a>初始化  
 当你的代码开始运行，您的对象变量初始化为`Nothing`。 这些声明中包含的初始化被重新初始化时执行的声明语句指定的值。  
  
 通过使用包括在声明中初始化[新建](../../../../visual-basic/language-reference/operators/new-operator.md)关键字。 下面的声明语句声明对象变量`testUri`和`ver`并向其分配特定的对象。 每个可以使用一种合适的类的重载构造函数来初始化对象。  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>解除关联  
 将对象变量设置为`Nothing`终止与任何特定对象的变量的关联。 这会防止意外更改通过更改变量的对象。 它还允许您测试对象变量是否指向有效的对象，如以下示例所示。  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 如果您的变量是指该对象是另一个应用程序中，该应用程序是否已终止或只是失效的对象无法确定此测试。  
  
 值为对象变量`Nothing`也称为*null 引用*。  
  
## <a name="current-instance"></a>当前实例  
 *当前实例*的对象是当前正在其中执行代码。 在过程内执行所有代码，因为当前实例是在其中调用该过程。  
  
 `Me`关键字作为对象变量引用当前实例。 如果不是一个过程[共享](../../../../visual-basic/language-reference/modifiers/shared.md)，可以使用`Me`关键字来获取当前实例的指针。 共享的过程不能与类的特定实例相关联。  
  
 使用`Me`对于当前的实例传递到另一个模块中的过程非常有用。 例如，假设你有多个 XML 文档，想要将一些标准文本添加到所有这些。 下面的示例定义一个过程来执行此操作。  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 然后，每个 XML 文档对象无法调用该过程，并作为参数传递它的当前实例。 下面的示例演示这一操作。  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>请参阅

- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [对象变量值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：声明对象变量并在 Visual Basic 中为其分配对象](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：使对象变量不引用任何实例](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
