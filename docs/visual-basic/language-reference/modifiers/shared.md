---
title: Shared (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 12c81a9a0651088a348afeaff3b71935d289da53
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816274"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
指定一个或多个声明的编程元素与类或结构在整体上，而不是与类或结构的特定实例相关联。  
  
## <a name="remarks"></a>备注  
  
## <a name="when-to-use-shared"></a>何时使用共享  
 共享的类或结构成员将其提供给每个实例，而非*非共享*，其中每个实例都需要其自己的副本。 这很有用，例如，如果变量的值适用于整个应用程序。 如果声明该变量为`Shared`、 所有实例都访问相同的存储位置，然后，如果一个实例更改变量的值，所有实例都都访问更新后的值。  
  
 共享不会更改成员的访问级别。 例如，可以共享类成员和专用 （可访问只能从类中），或非共享和公共。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>规则  
  
-   **声明上下文。** 只能在模块级别使用 `Shared`。 这意味着声明上下文`Shared`元素必须是类或结构，并且不能是源文件、 命名空间或过程。  
  
-   **组合的修饰符。** 不能指定`Shared`连同[重写](../../../visual-basic/language-reference/modifiers/overrides.md)， [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)， [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)， [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)，或[静态](../../../visual-basic/language-reference/modifiers/static.md)同一声明中。  
  
-   **访问。** 通过其类或结构的名称而不是类或结构的特定实例的变量名称限定其访问的共享的元素。 甚至不需要创建类或结构来访问它的共享的成员的实例。  
  
     下面的示例调用共享的过程<xref:System.Double.IsNaN%2A>公开的<xref:System.Double>结构。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **隐式共享。** 不能使用`Shared`修饰符[Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)，但常量被隐式共享。 同样，不能声明为模块或接口的成员`Shared`，但它们会被隐式共享。  
  
## <a name="behavior"></a>行为  
  
-   **存储。** 只有一次，无论多少或少数几个实例创建的类或结构，在内存中存储的共享的变量或事件。 同样，共享的过程或属性包含只有一组本地变量。  
  
-   **通过实例变量访问。** 就可以通过用包含类或结构的特定实例的变量的名称限定其访问的共享的元素。 虽然这通常按预期工作，编译器将生成一条警告消息，并使通过类或结构的名称，而不是变量的访问权限。  
  
-   **通过的实例表达式进行访问。** 如果通过一个表达式，返回其类或结构的实例访问共享的元素，编译器可让通过类或结构的名称，而不是计算表达式的访问权限。 如果你想要执行其他操作以及返回实例的表达式，这将会产生意外的结果。 下面的示例阐释了这一点。  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     在前面的示例中，编译器将生成一条警告消息的代码可访问共享的变量这两个时间`total`通过实例。 每种情况下它都使通过类直接访问`shareTotal`，而不进行使用的任何实例。 在对过程的预期调用的情况下`returnClass`，这意味着即使生成调用`returnClass`，因此不执行其他操作的显示"调用函数 returnClass()"。  
  
 `Shared` 修饰符可用于下面的上下文中：  
  
 [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [在 Visual Basic 中的生存期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [过程](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [结构](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [对象和类](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
