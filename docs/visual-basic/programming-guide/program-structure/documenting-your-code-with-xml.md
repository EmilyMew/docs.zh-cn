---
title: 使用 XML 将代码文档化 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 9b53b73afb9c6b793597c00fd2eb029b18bf1f9a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831574"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>使用 XML 将代码文档化 (Visual Basic)
在 Visual Basic 中，您可以记录你的代码使用 XML  
  
## <a name="xml-documentation-comments"></a>XML 文档注释  
 Visual Basic 提供了自动创建项目的 XML 文档的简单办法。 可以自动生成的类型和成员，XML 框架，然后为每个参数和其他备注中提供摘要、 描述性的文档。 通过适当的设置，XML 文档将自动发出到 XML 文件中使用与你的项目和.xml 扩展名相同的名称。 有关详细信息，请参阅 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
 可以使用或操作的资源以 XML 形式的 XML 文件。 此文件位于你的项目输出.exe 或.dll 文件所在的同一目录中。  
  
 XML 文档开头`'''`。 处理这些注释时存在一些限制：  
  
-   文档必须是格式正确的 XML。 如果 XML 的格式不正确，则会生成警告，并且文档文件包含条注释，指出遇到错误。  
  
-   开发人员可以随意创建自己的标记集。 没有一组推荐的标记 （请参阅本主题中的"相关章节"）。 部分建议标记具有特殊含义：  
  
    -   \<param> 标记用于描述参数。 如果使用，编译器将验证该参数是否存在，以及文档是否描述了所有参数。 如果验证失败，编译器会发出警告。  
  
    -   `cref` 属性可以附加到任何标记，以提供对代码元素的引用。 编译器验证此代码元素是否存在。 如果验证失败，编译器会发出警告。 编译器还将考虑所有`Imports`语句中所述的类型查找时`cref`属性。  
  
    -   \<摘要 > Visual Studio 中的 IntelliSense 使用标记以显示有关类型或成员的其他信息。  
  
## <a name="related-sections"></a>相关章节  
 有关创建带有文档注释的 XML 文件的详细信息，请参阅以下主题：  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)  
  
-   [处理 XML 文件](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [如何：创建 XML 文档](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio 中的 XML 工具](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>请参阅

- [使用 Visual Basic 开发应用程序](../../../visual-basic/developing-apps/index.md)
- [Visual Basic 编程指南](../../../visual-basic/programming-guide/index.md)
