---
title: 如何：在 XML 文本 (Visual Basic 中) 中嵌入表达式
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 31e79a8787978ffab2e35cd2827b80a8f1ed843e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841576"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>如何：在 XML 文本 (Visual Basic 中) 中嵌入表达式
您可以将 XML 文本与嵌入的表达式来创建 XML 文档、 片段或包含在运行时创建的内容的元素。 以下示例演示如何使用嵌入式的表达式在运行时填充元素内容、 属性和元素名称。  
  
 嵌入式表达式的语法是`<%=` `exp` `%>`，这是相同的语法的[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]使用。 有关详细信息，请参阅[XML 中的嵌入式表达式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 此外可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 来创建[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象。 有关详细信息，请参阅 <xref:System.Xml.Linq.XElement>。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-insert-text-as-element-content"></a>若要作为元素内容中插入文本  
  
-   下面的示例演示如何插入文本中包含的`contactName`变量之间的开始和结束的名称元素。  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     该示例产生下面的输出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>作为属性值中插入文本  
  
-   下面的示例演示如何插入中包含的文本`phoneType`变量的值作为`type`属性。  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     该示例产生下面的输出：  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>若要插入的元素名称的文本  
  
-   下面的示例演示如何插入文本中包含的`elementName`变量作为元素的名称。  
  
     创建元素时使用此技术，必须将它们与\</ > 标记。  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     该示例产生下面的输出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>请参阅

- [如何：创建 XML 文本](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [XML 中的嵌入式表达式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
