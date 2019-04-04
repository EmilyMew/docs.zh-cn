---
title: Visual Basic 中的 LINQ to XML 概述
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 91f622b9eecdd1aec8b9361493095e92a851988e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816169"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic 中的 LINQ to XML 概述
Visual Basic 提供的支持[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]通过 XML 文本和 XML 轴属性。 这使您要用于在 Visual Basic 代码中使用 XML 熟悉、 便利的语法。 *XML 文本*，可以在代码中直接包含 XML。 *XML 轴属性*使您能够访问子节点、 子代节点和属性的 XML 文本。 有关详细信息，请参阅[XML 文本概述](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)并[在 Visual Basic 中访问 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 内存中 XML 编程 API，专门用于充分利用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。 虽然可以调用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 直接、 仅 Visual Basic，可声明 XML 文本并直接访问 XML 轴属性。  
  
> [!NOTE]
>  在 ASP.NET 页面中的声明性代码中不支持 XML 文本和 XML 轴属性。 若要使用 Visual Basic XML 功能，请将代码放在 ASP.NET 应用程序中的代码隐藏页中。  
  
 ![视频链接](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "播放视频")相关视频演示，请参阅[如何开始使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)并[如何创建 Excel 电子表格使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。  
  
## <a name="creating-xml"></a>创建 XML  
 有两种方法在 Visual Basic 中创建 XML 树。 您可以声明 XML 文本直接在代码中，也可以使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 可以创建的树。 这两个进程都使代码能够反映 XML 树的最终结构。 例如，下面的代码示例创建一个 XML 元素：  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 有关详细信息，请参阅[在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。  
  
## <a name="accessing-and-navigating-xml"></a>访问和导航 XML  
 Visual Basic 提供了用于访问和导航 XML 结构的 XML 轴属性。 这些属性，可以通过指定的 XML 子元素名称来访问 XML 元素和属性。 或者，您可以显式调用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]用于导航和查找元素和属性的方法。 例如，下面的代码示例使用 XML 轴属性来指代的属性和 XML 元素的子元素。 代码示例使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询以检索子元素并输出为 XML 元素，从而有效地执行转换。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 有关详细信息，请参阅[在 Visual Basic 中访问 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
## <a name="xml-namespaces"></a>XML 命名空间  
 Visual Basic，可通过使用指定的全局 XML 命名空间的别名`Imports`语句。 下面的示例演示如何使用`Imports`语句导入的 XML 命名空间：  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 访问 XML 轴属性和声明的 XML 文档和元素的 XML 文本时，可以使用 XML 命名空间别名。  
  
 可以检索<xref:System.Xml.Linq.XNamespace>对象使用的特定命名空间前缀[GetXmlNamespace 运算符](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)。  
  
 有关详细信息，请参阅[Imports 语句 (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>在 XML 文本中使用 XML 命名空间  
 下面的示例演示如何创建<xref:System.Xml.Linq.XElement>使用全局命名空间的对象`ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic 编译器将 XML 文本中使用的 XML 命名空间中使用的 XML 表示法的等效代码包含 XML 命名空间别名为`xmlns`属性。 编译时上, 一节的示例中的代码生成实质上是相同的可执行代码如下面的示例：  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>使用 XML 命名空间中 XML 轴属性  
 在 XML 文本中声明的 XML 命名空间不可用于在 XML 轴属性中使用。 但是，可以使用 XML 轴属性使用全局命名空间。 使用冒号分隔的 XML 命名空间前缀和本地元素名称。 下面是一个示例：  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>请参阅

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中创建 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [在 Visual Basic 中访问 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [在 Visual Basic 中操控 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
