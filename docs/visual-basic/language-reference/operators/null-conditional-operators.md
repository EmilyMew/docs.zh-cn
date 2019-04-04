---
title: Null 条件运算符 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348760"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. 和？（） null 条件运算符 (Visual Basic)

测试是否为空的左操作数的值 (`Nothing`) 之前执行成员访问 (`?.`) 或索引 (`?()`); 操作返回`Nothing`如果左操作数的计算结果为`Nothing`。 请注意，在表达式中通常返回值类型，null 条件运算符返回<xref:System.Nullable%601>。

这些运算符可帮助您编写更少代码来处理 null 检查，尤其是当下降到数据结构。 例如：

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

有关比较，这些表达式而无需 null 条件运算符的第一个替代代码是：

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

NULL 条件运算符采用最小化求值策略。  如果条件成员访问和索引操作链中的一个操作返回`Nothing`，链的执行将停止的其余部分。  在以下示例中，`C(E)`如果未进行求值`A`， `B`，或`C`计算结果为`Nothing`。

```vb
A?.B?.C?(E);
```

Null 条件成员访问的另一个用途是在使用非常少的代码以线程安全的方式调用委托。  下面的示例定义两种类型，`NewsBroadcaster`和一个`NewsReceiver`。 新闻项发送到由接收方`NewsBroadcaster.SendNews`委托。

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

如果没有在元素`SendNews`调用列表，列出`SendNews`委托，则会引发<xref:System.NullReferenceException>。 Null 条件运算符之前代码，类似以下确保委托调用列表不是`Nothing`:

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

新的方法是要简单得多：  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

新方法是线程安全的，因为编译器生成的代码仅评估 `SendNews` 一次，从而使结果保持在临时变量中。 你需要显式调用 `Invoke` 方法，因为不存在 NULL 条件委托调用语法 `SendNews?(String)`。  

## <a name="see-also"></a>请参阅

- [运算符 (Visual Basic)](index.md)
- [Visual Basic 编程指南](../../../visual-basic/programming-guide/index.md)
- [Visual Basic 语言参考](../../../visual-basic/language-reference/index.md)
