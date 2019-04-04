---
title: XML 中的嵌入式表达式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 4c96665994a7e56bc70f72b66d5922f5a6472a13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827570"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中的嵌入式表达式 (Visual Basic)
嵌入的表达式，可以创建包含在运行时计算的表达式的 XML 文本。 嵌入式表达式的语法是`<%=` `expression` `%>`，这是相同的语法中使用[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]。  
  
 例如，您可以创建一个 XML 元素文本，组合嵌入式的表达式包含文字文本内容。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 如果`isbnNumber`包含整数 12345 并`modifiedDate`包含的日期 3/5/2006，当此代码执行时，值`book`是：  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>嵌入的表达式的位置和验证  
 嵌入的表达式只能出现在 XML 文本表达式中的某些位置。 可以返回该类型的表达式的表达式位置控件以及如何`Nothing`进行处理。 下表介绍了允许的位置和嵌入表达式的类型。  
  
|在文本中的位置|表达式的类型|处理 `Nothing`|  
|---|---|---|  
|XML 元素名称|<xref:System.Xml.Linq.XName>|Error|  
|XML 元素内容|`Object` 或数组 `Object`|忽略|  
|XML 元素属性名称|<xref:System.Xml.Linq.XName>|错误，除非也是属性值 `Nothing`|  
|XML 元素特性值|`Object`|忽略的属性声明|  
|XML 元素特性|<xref:System.Xml.Linq.XAttribute> 或一系列 <xref:System.Xml.Linq.XAttribute>|忽略|  
|XML 文档根元素|<xref:System.Xml.Linq.XElement> 或其中一个集合<xref:System.Xml.Linq.XElement>对象和任意数量<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>对象|忽略|  
  
-   XML 元素名称中嵌入表达式的示例：  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
-   XML 元素的内容中嵌入表达式的示例：  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
-   XML 元素属性名称中嵌入表达式的示例：  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
-   嵌入表达式的 XML 元素特性值中的示例：  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
-   XML 元素特性中嵌入表达式的示例：  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
-   XML 文档的根元素中的嵌入式表达式的示例：  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 如果启用`Option Strict`，编译器会检查每个嵌入表达式的类型加宽到所需的类型。 唯一的例外是在代码运行时验证 XML 文档的根元素。 如果编译而无需`Option Strict`，可以将嵌入类型的表达式`Object`和在运行时验证它们的类型。  
  
 可选的内容的位置中嵌入表达式包含`Nothing`将被忽略。 这意味着不需要检查该元素内容中，属性值，并且数组元素不是`Nothing`使用 XML 文本之前。 所需的值，例如元素和属性名称不能为`Nothing`。  
  
 有关在特定类型的文本中使用嵌入式的表达式的详细信息，请参阅[XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="scoping-rules"></a>作用域规则  
 编译器将每个 XML 文本转换为相应的文本类型的构造函数调用。 文本内容和 XML 文本中的嵌入式的表达式作为参数传递给构造函数。 这意味着所有 Visual Basic 编程元素可用于 XML 文本也都都可在其嵌入式表达式。  
  
 在 XML 文本中，可以访问的 XML 命名空间前缀声明与`Imports`语句。 您可以声明新的 XML 命名空间前缀，或现有的 XML 命名空间前缀，使用的元素中的卷影`xmlns`属性。 新的命名空间是可用的子节点的该元素，而不是属于 XML 文本中嵌入的表达式。  
  
> [!NOTE]
>  当使用声明 XML 命名空间前缀`xmlns`命名空间属性的属性值必须是常量字符串。 在这方面，使用`xmlns`属性就像使用`Imports`语句声明 XML 命名空间。 不能使用嵌入式的表达式来指定 XML 命名空间值。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports 语句（.NET 命名空间和类型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML 文本概述](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
