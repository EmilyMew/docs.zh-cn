---
title: Namespace 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 7f6b976af7933b3895f6992488d2d1532a8fc2f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820927"
---
# <a name="namespace-statement"></a>Namespace 语句
声明命名空间的名称，并使遵循声明在该命名空间中进行编译的源代码。  
  
## <a name="syntax"></a>语法  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>部件  
 Global  
 可选。 允许你定义你的项目根命名空间之外。 请参阅[在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `name`  
 必需。 用于标识命名空间的唯一名称。 必须是有效的 Visual Basic 标识符。 有关详细信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `componenttypes`  
 可选。 构成该命名空间的元素。 这些包括但不限于枚举、 结构、 接口、 类、 模块、 委托和其他命名空间。  
  
 `End Namespace`  
 终止`Namespace`块。  
  
## <a name="remarks"></a>备注  
 命名空间用作组织的系统。 它们提供一种方法来进行分类并提供向其他程序和应用程序公开的编程元素。 请注意，命名空间不是*类型*类或结构是在意义上，不能声明为具有一个命名空间的数据类型的编程元素。  
  
 所有编程元素声明后`Namespace`语句属于该命名空间。 Visual Basic 会继续将编译到最后一个声明的命名空间的元素，直到它遇到上述任何`End Namespace`语句或另一个`Namespace`语句。  
  
 如果已定义一个命名空间，甚至在项目之外，您可以向其添加编程元素。 若要执行此操作，应使用`Namespace`语句，以指示 Visual Basic 将编译到该命名空间的元素。  
  
 可以使用`Namespace`仅在文件或命名空间级别语句。 这意味着*声明上下文*的命名空间必须是源文件或另一个命名空间，且不能为类、 结构、 模块、 接口或过程。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以声明一个命名空间包含在另一个。 可以声明，但请记住，当其他代码访问最内部的命名空间中声明的元素，它必须使用包含嵌套层次结构中的所有命名空间名称的限定字符串的嵌套级别没有严格限制。  
  
## <a name="access-level"></a>访问级别  
 命名空间均被视为如同它们具有`Public`访问级别。 从任意位置在同一项目中的代码、 其他引用该项目的项目和项目生成任何程序集，可以访问命名空间。  
  
 在命名空间级别，这意味着命名空间中、 但在任何其他元素声明的编程元素可以具有`Public`或`Friend`访问。 如果未指定，使用此类的访问级别元素`Friend`默认情况下。 可以在命名空间级别声明的元素包括类、 结构、 模块、 接口、 枚举和委托。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## <a name="root-namespace"></a>根 Namespace  
 在项目中的所有命名空间名称基于*根命名空间*。 Visual Studio 针对项目中的所有代码，将项目名称指定为默认根命名空间。 例如，如果项目命名为 `Payroll`，则其编程元素属于命名空间 `Payroll`。 如果声明`Namespace funding`，该命名空间的完整名称是`Payroll.funding`。  
  
 如果你想要指定现有的命名空间中`Namespace`语句，如在泛型列表类示例中，可以将根命名空间设置为 null 值。 若要执行此操作，请单击**项目属性**从**项目**菜单，然后清除**根命名空间**条目，以便此框为空。 如果您没有不这样做在泛型列表类的示例中，将需要 Visual Basic 编译器`System.Collections.Generic`作为新项目中的命名空间`Payroll`，使用的完整名称`Payroll.System.Collections.Generic`。  
  
 或者，可以使用`Global`关键字来引用在项目外部定义的命名空间的元素。 这样就可以保留你的项目名称作为根命名空间。 这将减少无意中将编程元素以及现有命名空间的可能性。 有关详细信息，请参阅中的"全局关键字中完全限定名称"部分[在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 `Global`还 Namespace 语句中使用关键字。 这将允许你定义项目根命名空间之外的命名空间。 有关详细信息，请参阅中的"全局关键字在 Namespace 语句"一节[在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
 **故障排除。** 根命名空间可能会导致意外的命名空间名称的串联。 如果在项目外部定义的命名空间的引用，Visual Basic 编译器可以 construe 它们作为根命名空间中的嵌套命名空间。 在这种情况下，编译器无法识别已在外部命名空间中定义的任何类型。 若要避免此问题，请设置根命名空间为"根 Namespace，"中所述的 null 值，或使用`Global`关键字来访问外部命名空间的元素。  
  
## <a name="attributes-and-modifiers"></a>特性和修饰符  
 不能将特性应用到的命名空间。 特性提供信息对程序集的元数据，这并无意义的源分类器，例如命名空间。  
  
 不能应用到命名空间的任何访问或过程修饰符或任何其他修饰符。 由于它不是类型，这些修饰符不是有意义的。  
  
## <a name="example"></a>示例  
 下面的示例声明两个命名空间，嵌套在另一个。  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>示例  
 下面的示例在单个行上声明多个嵌套的命名空间，它等效于前面的示例。  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>示例  
 以下示例将访问的上一示例中定义的类。  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>示例  
 下面的示例定义一个新的泛型列表类的框架，并将其添加到<xref:System.Collections.Generic?displayProperty=nameWithType>命名空间。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>请参阅

- [Imports 语句（.NET 命名空间和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [已声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)
