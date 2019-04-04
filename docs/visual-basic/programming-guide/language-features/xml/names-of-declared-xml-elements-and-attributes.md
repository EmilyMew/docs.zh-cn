---
title: 已声明的 XML 元素和特性的名称 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819679"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>已声明的 XML 元素和特性的名称 (Visual Basic)
本主题提供用于命名 XML 元素和属性在 XML 文本中的 Visual Basic 指南。  在 XML 文本，可以指定本地名称或限定的名称。 限定的名由 XML 命名空间前缀、 冒号和本地名称组成。 有关 XML 命名空间前缀的详细信息，请参阅[XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="rules"></a>规则  
 本地名称的元素或属性在 Visual Basic 中的为必须遵守以下规则。  
  
-   它可以开始与命名空间。 它必须以字母字符或下划线开头 (`_`)。  
  
-   它必须包含仅字母字符、 十进制数字、 下划线、 句点 （.） 和连字符 （-）。  
  
-   它不能超过 1024 个字符。  
  
-   出现在名称中的冒号指示命名空间划分。 因此，可以使用冒号只能用于指定特定名称的 XML 命名空间。  
  
 此外，您应该遵守以下准则。  
  
-   XML 1.0 规范保留字符串的任何大小写变体"xml"开头的所有名称。 因此，不要使用这些名称用作元素和属性名称。  
  
### <a name="name-length-guidelines"></a>名称长度准则  
 在实践中，名称应尽可能短时仍然能够清楚地标识元素的特性。 这可提高你的代码的可读性，并减少行长度和源文件大小。  
  
 但是，你的名称不应太短，它不会不充分描述的元素或你的代码如何使用它。 这一点对于提高代码的可读性。 如果其他人正在尝试理解它，或者如果您自己正在寻求通过它您在编写之后很长时间，相应的元素名称可以节省时间。  
  
## <a name="case-sensitivity-in-names"></a>在名称中区分大小写  
 XML 元素名称都区分大小写。 这意味着当 Visual Basic 编译器在比较两个不同的只有字母大小写的名称，将它们解释为不同的名称。 例如，它可解释`ABC`和`abc`作为引用不同的元素。  
  
## <a name="xml-namespaces"></a>XML 命名空间  
 在创建的 XML 元素文本时，可以指定元素名称的 XML 命名空间前缀。 有关详细信息，请参阅[XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
