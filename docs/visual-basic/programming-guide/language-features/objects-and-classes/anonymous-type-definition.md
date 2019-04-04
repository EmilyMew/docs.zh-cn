---
title: 匿名类型定义 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 832d56f5c51aea87185f36ec306c3fec036a40e0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825542"
---
# <a name="anonymous-type-definition-visual-basic"></a>匿名类型定义 (Visual Basic)
在响应的匿名类型的实例声明时，编译器会创建包含类型的指定的属性的新类定义。  
  
## <a name="compiler-generated-code"></a>编译器生成的代码  
 有关的以下定义`product`，编译器会创建一个包含属性的新类定义`Name`， `Price`，和`OnHand`。  
  
 [!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]  
  
 类定义包含类似于下面的属性定义。 请注意，没有任何`Set`键属性的方法。 键属性的值是只读的。  
  
```vb  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 此外，匿名类型定义包含一个默认构造函数。 不允许需要参数的构造函数。  
  
 如果匿名类型声明包含至少一个键属性，类型定义将重写继承的三个成员<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 如果声明没有键属性，仅<xref:System.Object.ToString%2A>被重写。 重写提供以下功能：  
  
-   `Equals` 返回`True`如果两个匿名类型实例是相同的实例，或如果满足以下条件：  
  
    -   它们具有相同数量的属性。  
  
    -   在具有相同名称的相同顺序中声明的属性和相同的推断类型。 名称比较不区分大小写。  
  
    -   在至少一个属性是键属性和`Key`关键字应用于相同的属性。  
  
    -   键属性的每个相应的对比较返回`True`。  
  
     例如，在以下示例中，`Equals`将返回`True`仅`employee01`和`employee08`。 前面每行指定新的实例不匹配的原因的注释`employee01`。  
  
     [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]  
  
-   `GetHashcode` 提供了相应唯一的 GetHashCode 算法。 该算法使用只有键属性来计算哈希代码。  
  
-   `ToString` 返回连接的属性值的字符串，如下面的示例中所示。 包含密钥和非键属性。  
  
     [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]  
  
 显式命名的匿名类型属性不能与这些生成的方法发生冲突。 也就是说，不能使用`.Equals`， `.GetHashCode`，或`.ToString`命名属性。  
  
 至少包含一个匿名类型定义的键属性还实现<xref:System.IEquatable%601?displayProperty=nameWithType>接口，其中`T`是匿名类型的类型。  
  
> [!NOTE]
>  匿名类型声明创建同一匿名类型，仅当它们发生在同一程序集、 其属性具有相同的名称和相同的推断类型、 相同顺序声明的属性和相同的属性标记为键属性。  
  
## <a name="see-also"></a>请参阅

- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [如何：推断属性名和匿名类型声明中的类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
