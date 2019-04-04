---
title: Of 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823436"
---
# <a name="of-clause-visual-basic"></a>Of 子句 (Visual Basic)
引入了`Of`子句，用于标识*的类型形参*上*泛型*类、 结构、 接口、 委托或过程。 有关泛型类型的信息，请参阅[在 Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。  
  
## <a name="using-the-of-keyword"></a>使用的关键字  
 下面的代码示例使用`Of`关键字来定义采用两个类型参数的类的轮廓。 它*约束，使之*`keyType`参数<xref:System.IComparable>接口，这意味着使用的代码必须提供实现一个类型实参<xref:System.IComparable>。 这是必需的以便`add`过程可以调用<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>方法。 有关约束的详细信息，请参阅 [Type List](../../../visual-basic/language-reference/statements/type-list.md)。  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 如果您完成前面的类定义，可以构造各种`dictionary`从它的类。 提供给类型`entryType`和`keyType`确定哪种类型的条目类保存并与每个条目关联哪种类型的密钥。 由于该约束，必须提供给`keyType`实现的类型<xref:System.IComparable>。  
  
 下面的代码示例创建一个对象，保存`String`条目并将关联`Integer`其中每个密钥。 `Integer` 实现<xref:System.IComparable>，因此在满足约束`keyType`。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 `Of` 关键字可用于以下上下文中：  
  
 [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate 语句](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- <xref:System.IComparable>
- [类型列表](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
