---
title: Imports 语句-.NET Namespace 和类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 4574bab62ca6d095ab66c17bf186da5f3d79bfb7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826517"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports 语句（.NET 命名空间和类型）
使类型名称而无需命名空间限定引用。  
  
## <a name="syntax"></a>语法  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`aliasname`|可选。 *导入别名*或名称的代码可以指`namespace`而不是完全限定字符串。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`namespace`|必需。 正在导入的命名空间完全限定的名称。 可以命名空间的字符串嵌套到任意级别。|  
|`element`|可选。 命名空间中声明的编程元素的名称。 可以是任何容器元素。|  
  
## <a name="remarks"></a>备注  
 `Imports`语句启用直接引用给定命名空间中包含的类型。  
  
 你可以提供单个命名空间名称或嵌套的命名空间的字符串。 每个嵌套的命名空间从下一步的更高级别命名空间用句点隔开 (`.`)，如下面的示例所示。  
  
 `Imports System.Collections.Generic`  
  
 每个源文件可以包含任意数量的`Imports`语句。 这些必须遵循的任何选项声明，如`Option Strict`语句，并且它们必须编程元素位于任何声明之前，如`Module`或`Class`语句。  
  
 可以使用`Imports`仅在文件级别。 这意味着导入声明上下文必须是源文件，且不能为命名空间、 类、 结构、 模块、 接口、 过程或块。  
  
 请注意，`Imports`语句不会将元素从其他项目和程序集提供给你的项目。 导入不会替代设置的引用。 而只会删除需要限定已可供你的项目的名称。 详细信息，请参阅"导入包含元素"中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
> [!NOTE]
>  您可以定义隐式`Imports`通过使用语句[引用页上，项目设计器 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。 有关详细信息，请参阅[如何：添加或删除导入命名空间 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。  
  
## <a name="import-aliases"></a>导入别名  
 *导入别名*定义命名空间或类型的别名。 需要使用一个或多个命名空间中声明了一个同名的项时，导入别名是非常有用。 详细信息和示例，请参阅"符合条件的元素名称"中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 不应声明在模块级别具有相同的名称成员`aliasname`。 如果这样做，Visual Basic 编译器将使用`aliasname`仅对声明的成员且不能将其识别为某个导入别名。  
  
 尽管用于声明以导入别名的语法类似的用于导入 XML 命名空间前缀，则结果将不同。 导入别名可以用作在代码中，表达式，而 XML 命名空间前缀可以用于只能在 XML 文本或 XML 轴属性中作为前缀限定的元素或属性名称。  
  
### <a name="element-names"></a>元素名称  
 如果提供`element`，则它必须表示*容器元素*，也就是说，可以包含其他元素的编程元素。 容器元素包括类、 结构、 模块、 接口和枚举。  
  
 提供的元素的作用域`Imports`语句取决于是否指定`element`。 如果仅指定`namespace`，所有具有唯一名为该命名空间的成员和该命名空间中的容器元素的成员，是无需限定即可。 如果同时指定`namespace`和`element`，只有该元素的成员是无需限定即可。  
  
## <a name="example"></a>示例  
 下面的示例通过使用在 C:\ 目录中返回的所有文件夹<xref:System.IO.DirectoryInfo>类。  
  
 没有代码`Imports`语句的文件的顶部。 因此， `DirectoryInfo`， <xref:System.Text.StringBuilder>，和<xref:Microsoft.VisualBasic.ControlChars.CrLf>所有完全限定的命名空间的引用。  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>示例  
 下面的示例包括`Imports`引用的命名空间的语句。 因此，类型不需要用命名空间加以完全限定。  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>示例  
 下面的示例包括`Imports`为被引用的命名空间创建别名的语句。 类型别名进行限定。  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>示例  
 下面的示例包括`Imports`语句创建引用类型的别名。 使用别名来指定的类型。  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>请参阅

- [Namespace 语句](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [引用和 Imports 语句](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports 语句（XML 命名空间）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [对已声明元素的引用](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
