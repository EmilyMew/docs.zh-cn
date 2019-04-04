---
title: 如何：创建 XML 文本 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 836ec4390e7675effe57c75c79768272d66925a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836853"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>如何：创建 XML 文本 (Visual Basic)
通过使用 XML 文本，可以直接在代码中创建 XML 文档、 片段或元素。 本主题中的示例演示如何创建 XML 元素具有三个子元素，以及如何创建 XML 文档。  
  
 此外可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 来创建[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象。 有关详细信息，请参阅 <xref:System.Xml.Linq.XElement>。  
  
### <a name="to-create-an-xml-element"></a>若要创建一个 XML 元素  
  
-   使用 XML 文本语法，这是实际的 XML 语法相同创建内嵌的 XML。  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     运行代码。 此代码的输出为：  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>若要创建 XML 文档  
  
-   创建内联 XML 文档。 以下代码将创建具有文本语法、 XML 声明、 处理指令、 注释和一个包含另一个元素的元素的 XML 文档。  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     运行代码。 此代码的输出为：  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>请参阅

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
