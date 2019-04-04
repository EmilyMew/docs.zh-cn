---
title: 如何：声明结构 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7fc4aed4d405729b64a2f7ba772cdd794df40f2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825087"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>如何：声明结构 (Visual Basic)
在开始使用在结构声明[Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)，并结束与`End Structure`语句。 这两个语句之间必须声明至少一个*元素*。 元素可以是任何数据类型，但至少一个必须为非共享的变量或非共享、 非自定义事件。  
  
 无法初始化任何在结构声明中的结构元素。 声明变量为结构类型时，将值的元素分配通过它们访问通过变量。  
  
 结构和类之间的差异的讨论，请参阅[结构和类](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 出于演示目的，假设你想要跟踪的员工的名称、 电话分机和薪金。 一种结构，可在一个变量执行此操作。  
  
### <a name="to-declare-a-structure"></a>若要声明结构  
  
1.  创建的开始和结束语句的结构。  
  
     可以指定的结构使用的访问级别[公共](../../../../visual-basic/language-reference/modifiers/public.md)，[受保护](../../../../visual-basic/language-reference/modifiers/protected.md)，[友元](../../../../visual-basic/language-reference/modifiers/friend.md)，或者[专用](../../../../visual-basic/language-reference/modifiers/private.md)关键字，或者您可以让它默认为`Public`。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  将元素添加到结构的正文。  
  
     一种结构必须具有至少一个元素。 必须声明每个元素，并为其指定访问级别。 如果您使用[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)而无需任何关键字，可访问性默认为`Public`。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary`前面的示例中的字段是`Private`，这意味着它是结构之外，甚至自包含类不能访问。 但是，`giveRaise`过程是`Public`，因此它可以从调用，结构之外。 同样，你可以将提升`salaryReviewTime`从结构之外的事件。  
  
     除了变量，还`Sub`过程和事件，您还可以定义常量、`Function`过程和结构中的属性。 您可以指定最多一个属性作为*默认属性*，提供它采用至少一个自变量。 您可以处理的事件[共享](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`过程。 有关详细信息，请参阅[如何：声明和调用默认属性在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [复合数据类型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [结构变量](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [结构和其他编程元素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [结构和类](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [用户定义的数据类型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
