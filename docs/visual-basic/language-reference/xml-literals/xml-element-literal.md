---
title: XML 元素文本 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 7bd47d2461ba86dfbd1d5ff5993382914116f9ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842247"
---
# <a name="xml-element-literal-visual-basic"></a>XML 元素文本 (Visual Basic)

表示的文字值<xref:System.Xml.Linq.XElement>对象。  
  
## <a name="syntax"></a>语法  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>部件  
  
-   `<`  
  
     必需。 此时会打开起始元素标记。  
  
-   `name`  
  
     必需。 元素名称。 格式为以下值之一：  
  
    -   对于元素名称，窗体的文字文本`[ePrefix:]eName`，其中：  
  
        |部件|描述|  
        |---|---|  
        |`ePrefix`|可选。 元素的 XML 命名空间前缀。 必须使用定义的全局 XML 命名空间`Imports`语句文件中或在项目级别或在此元素或父元素中定义的本地 XML 命名空间。|  
        |`eName`|必需。 元素名称。 格式为以下值之一：<br /><br /> -文字文本。 请参阅[声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />嵌入形式的表达式`<%= eNameExp %>`。 类型`eNameExp`必须是`String`类型或类型的隐式转换为<xref:System.Xml.Linq.XName>。|  
  
    -   在窗体的嵌入式表达式`<%= nameExp %>`。 类型`nameExp`必须是`String`或隐式转换为类型<xref:System.Xml.Linq.XName>。 元素的结束标记中不允许嵌入的表达式。  
  
-   `attributeList`  
  
     可选。 在文本中声明的属性列表。  
  
     `attribute [ attribute ... ]`  
  
     每个`attribute`具有以下语法之一：  
  
    -   属性指定的窗体`[aPrefix:]aName=aValue`，其中：  
  
        |部件|描述|  
        |---|---|  
        |`aPrefix`|可选。 该属性的 XML 命名空间前缀。 必须使用定义的全局 XML 命名空间`Imports`语句或在此元素或父元素中定义的本地 XML 命名空间。|  
        |`aName`|必需。 属性的名称。 格式为以下值之一：<br /><br /> -文字文本。 请参阅[声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。<br />嵌入形式的表达式`<%= aNameExp %>`。 类型`aNameExp`必须是`String`类型或类型的隐式转换为<xref:System.Xml.Linq.XName>。|  
        |`aValue`|可选。 属性的值。 格式为以下值之一：<br /><br /> -文字文本，用引号括起来。<br />嵌入形式的表达式`<%= aValueExp %>`。 允许使用任何类型。|  
  
    -   在窗体的嵌入式表达式`<%= aExp %>`。  
  
-   `/>`  
  
     可选。 指示该元素为空元素，而无需内容。  
  
-   `>`  
  
     必需。 结束开始标记或空元素标记。  
  
-   `elementContents`  
  
     可选。 元素的内容。  
  
     `content [ content ... ]`  
  
     每个`content`可以是以下之一：  
  
    -   文字文本。 中的所有空白`elementContents`变得很重要，如果没有任何文字文本。  
  
    -   在窗体的嵌入式表达式`<%= contentExp %>`。  
  
    -   XML 元素文本。  
  
    -   XML 注释文本。 请参阅[XML 注释文本](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。  
  
    -   XML 处理指令文本。 请参阅[XML 处理指令文本](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。  
  
    -   XML CDATA 文本。 请参阅[XML CDATA 文本](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)。  
  
-   `</[name]>`  
  
     可选。 表示元素的结束标记。 可选`name`嵌入表达式的结果时不允许使用参数。  
  
## <a name="return-value"></a>返回值  
 一个 <xref:System.Xml.Linq.XElement> 对象。  
  
## <a name="remarks"></a>备注  
 可以使用 XML 元素文本语法创建<xref:System.Xml.Linq.XElement>在代码中的对象。  
  
> [!NOTE]
>  XML 文本可以跨多个行，而无需使用行继续符。 此功能，可将内容从 XML 文档复制并粘贴直接到 Visual Basic 程序。  
  
 嵌入表达式的窗体`<%= exp %>`，可以将动态信息添加到 XML 元素文本。 有关详细信息，请参阅[XML 中的嵌入式表达式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 Visual Basic 编译器将调用转换为 XML 元素文本<xref:System.Xml.Linq.XElement.%23ctor%2A>构造函数，如果是必需的<xref:System.Xml.Linq.XAttribute.%23ctor%2A>构造函数。  
  
## <a name="xml-namespaces"></a>XML 命名空间  
 您必须使用在代码中多次的同一命名空间中的元素创建 XML 文本时，XML 命名空间前缀非常有用。 可以使用全局 XML 命名空间前缀，使用定义`Imports`语句或通过使用定义的本地前缀`xmlns:xmlPrefix="xmlNamespace"`特性语法。 有关详细信息，请参阅[Imports 语句 (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
 XML 命名空间的范围规则，根据本地前缀优先于全局前缀。 但是，如果 XML 文本定义的 XML 命名空间，该命名空间不可用到嵌入式表达式中出现的表达式。 嵌入式的表达式可以访问仅全局 XML 命名空间。  
  
 Visual Basic 编译器将转换为生成的代码中的一个本地命名空间定义 XML 文本使用每个全局 XML 命名空间。 生成的代码中不显示未使用的全局 XML 命名空间。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建简单的 XML 元素具有两个嵌套的空元素。  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 此示例显示以下文本。 请注意，文本会保留为空元素的结构。  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用嵌入式的表达式来命名元素和创建属性。  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 此代码显示以下文本：  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>示例  
 下面的示例声明 `ns` 作为 XML 命名空间前缀。 然后，它使用的命名空间前缀来创建 XML 文本，并显示元素的最终形式。  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 此代码显示以下文本：  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 请注意，编译器为 XML 命名空间的前缀定义转换的全局 XML 命名空间前缀。 \<Ns:middle > 元素重新定义的 XML 命名空间前缀\<ns:inner1 > 元素。 但是， \<ns:inner2 > 元素使用定义的命名空间`Imports`语句。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- [已声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML 注释文本](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML CDATA 文本](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中的嵌入式表达式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports 语句（XML 命名空间）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
