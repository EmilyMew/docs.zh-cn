---
title: XML 文档文本 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814622"
---
# <a name="xml-document-literal-visual-basic"></a>XML 文档文本 (Visual Basic)
一个文本表示<xref:System.Xml.Linq.XDocument>对象。  
  
## <a name="syntax"></a>语法  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`encoding`|可选。 声明的编码文档使用的文字文本。|  
|`standalone`|可选。 文字文本。 必须为"yes"或"no"。|  
|`piCommentList`|可选。 XML 处理指令和 XML 注释的列表。 采用以下格式：<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 每个`piComment`可以是以下之一：<br /><br /> -   [XML 处理指令文本](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。<br />-   [XML 注释文本](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。|  
|`rootElement`|必需。 文档的根元素。 格式为以下值之一：<br /><br /> <ul><li>[XML 元素文本](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</li><li>嵌入形式的表达式`<%=` `elementExp` `%>`。 `elementExp`返回以下值之一：<br /><br /> <ul><li>一个 <xref:System.Xml.Linq.XElement> 对象。</li><li>一个集合，包含一个<xref:System.Xml.Linq.XElement>对象和任意数量的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>对象。</li></ul></li></ul><br /> 有关详细信息，请参阅[XML 中的嵌入式表达式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
  
## <a name="return-value"></a>返回值  
 一个 <xref:System.Xml.Linq.XDocument> 对象。  
  
## <a name="remarks"></a>备注  
 XML 文档文本的文本开头的 XML 声明标识。 尽管每个 XML 文档文本必须有且只有一个根 XML 元素，但它可以有任意数量的 XML 处理指令和 XML 注释。  
  
 XML 文档文本不能出现在一个 XML 元素。  
  
> [!NOTE]
>  XML 文本可以跨多个行，而无需使用行继续符。 这使您可以从 XML 文档中复制内容并将其粘贴到 Visual Basic 程序直接。  
  
 Visual Basic 编译器将调用转换为 XML 文档文本<xref:System.Xml.Linq.XDocument.%23ctor%2A>和<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>构造函数。  
  
## <a name="example"></a>示例  
 以下示例创建具有 XML 声明、 处理指令、 注释和一个包含另一个元素的元素的 XML 文档。  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML 处理指令文本](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [XML 注释文本](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML 元素文本](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中的嵌入式表达式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
