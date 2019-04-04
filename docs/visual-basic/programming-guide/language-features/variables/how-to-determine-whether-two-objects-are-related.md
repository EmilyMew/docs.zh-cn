---
title: 如何：确定两个对象是否相关 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: c4ff7c8e616c9126eae11a23e001c219dcbc0907
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819198"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>如何：确定两个对象是否相关 (Visual Basic)
您可以比较两个对象以确定此关系，如果有，在创建的类之间。 <xref:System.Type.IsInstanceOfType%2A>方法<xref:System.Type?displayProperty=nameWithType>类返回`True`或如果指定的类继承自当前类中，如果当前类型是指定类所支持的接口。  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>若要确定是否一个对象继承自另一个对象的类或接口  
  
1.  您认为在对象上可能具有的基类型，则调用<xref:System.Object.GetType%2A>方法。  
  
2.  上<xref:System.Type?displayProperty=nameWithType>返回的对象<xref:System.Object.GetType%2A>，调用<xref:System.Type.IsInstanceOfType%2A>方法。  
  
3.  中的参数列表<xref:System.Type.IsInstanceOfType%2A>，指定你认为对象可能是派生类型。  
  
     <xref:System.Type.IsInstanceOfType%2A> 返回`True`如果从其自变量类型继承<xref:System.Type?displayProperty=nameWithType>对象类型。  
  
## <a name="example"></a>示例  
 下面的示例确定一个对象是否表示派生自另一个对象的类的类。  
  
```  
Public Class baseClass  
End Class  
Public Class derivedClass : Inherits baseClass  
End Class  
Public Class testTheseClasses  
    Public Sub seeIfRelated()  
        Dim baseObj As Object = New baseClass()  
        Dim derivedObj As Object = New derivedClass()  
        Dim related As Boolean  
        related = baseObj.GetType().IsInstanceOfType(derivedObj)  
        MsgBox(CStr(related))  
    End Sub  
End Class  
```  
  
 请注意对的调用中的两个对象变量的意外的位置<xref:System.Type.IsInstanceOfType%2A>。 假定的基类型用于生成<xref:System.Type?displayProperty=nameWithType>类，并假定的派生的类型作为参数传递<xref:System.Type.IsInstanceOfType%2A>方法。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：确定两个对象是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
