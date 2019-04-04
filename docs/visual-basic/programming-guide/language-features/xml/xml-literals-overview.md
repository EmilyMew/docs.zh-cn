---
title: XML 文本概述 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: a7b70669131ae35135088418e4b33b3ae289d322
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839881"
---
# <a name="xml-literals-overview-visual-basic"></a>XML 文本概述 (Visual Basic)
*XML 文本*允许您将 XML 直接并入您的 Visual Basic 代码。 使用 XML 文本语法表示[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象，它是类似于 XML 1.0 语法。 这使得更轻松地以编程方式创建 XML 元素和文档，因为你的代码具有相同的结构与最终的 XML。  
  
 Visual Basic 编译 XML 文本转换[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供用于创建和操作 XML，简单对象模型和此模型完美集成[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。 有关详细信息，请参阅 <xref:System.Xml.Linq.XElement>。  
  
 可以在 XML 文本中嵌入的 Visual Basic 表达式。 在运行时，应用程序创建[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]为每个文本合并嵌入表达式的值的对象。 这允许您指定在 XML 文本内的动态内容。 有关详细信息，请参阅[XML 中的嵌入式表达式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 有关使用 XML 文本语法和 XML 1.0 语法之间的差异的详细信息，请参阅[XML 文本和 XML 1.0 规范](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>简单的文本  
 您可以创建[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]通过键入或粘贴中有效的 XML 在 Visual Basic 代码中的对象。 XML 元素文本返回<xref:System.Xml.Linq.XElement>对象。 有关详细信息，请参阅[XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)并[XML 文本和 XML 1.0 规范](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。 以下示例创建具有多个子元素的 XML 元素。  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 可以通过启动 XML 文本与创建 XML 文档`<?xml version="1.0"?>`，如以下示例所示。 XML 文档文本返回<xref:System.Xml.Linq.XDocument>对象。 有关详细信息，请参阅[XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
>  在 Visual Basic 中的 XML 文本语法不是与 XML 1.0 规范中的语法相同。 有关详细信息，请参阅[XML 文本和 XML 1.0 规范](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行继续符  
 XML 文本可以跨多个行，而无需使用行继续符 （空间下划线输入顺序）。 这使得更轻松地比较在代码中使用 XML 文档的 XML 文本。  
  
 编译器将作为 XML 文本的一部分行继续符。 因此，应使用的空间下划线输入序列，仅当它位于[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象。  
  
 但是，如果，则需要行继续符的嵌入式表达式中有多行表达式。 有关详细信息，请参阅[XML 中的嵌入式表达式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>在 XML 文本中嵌入的查询  
 您可以在嵌入式表达式中使用查询。 当执行此操作时，查询返回的元素添加到 XML 元素。 这允许您添加到 XML 文本的动态内容，例如用户的查询的结果。  
  
 例如，下面的代码使用嵌入式的查询的成员从创建 XML 元素`phoneNumbers2`数组，然后将这些元素添加为子级`contact2`。  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>编译器如何从 XML 文本创建对象  
 Visual Basic 编译器将 XML 文本转换为等效的调用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]构造函数来构建[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]对象。 例如，Visual Basic 编译器将转换为下面的代码示例调用到<xref:System.Xml.Linq.XProcessingInstruction>XML 版本指令，构造函数调用到<xref:System.Xml.Linq.XElement>构造函数`<contact>`， `<name>`，和`<phone>`元素，并调用<xref:System.Xml.Linq.XAttribute>构造函数`type`属性。 具体而言，在下面的示例中提供的属性，Visual Basic 编译器将调用<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>构造函数两次。 第一个的值将传递`type`有关`name`参数和值`home`为`value`参数。 第二个也将值`type`有关`name`参数，但值`work`为`value`参数。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中的嵌入式表达式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML 文档文本](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 元素文本](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 文本](../../../../visual-basic/language-reference/xml-literals/index.md)
