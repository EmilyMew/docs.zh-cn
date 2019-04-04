---
title: 命名空间概述 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: 45328fe0ac549086b8abea22c42c7be37fb12b3c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831953"
---
# <a name="namespaces-overview-linq-to-xml"></a>命名空间概述 (LINQ to XML)
本主题介绍命名空间、<xref:System.Xml.Linq.XName> 类和 <xref:System.Xml.Linq.XNamespace> 类。  
  
## <a name="xml-names"></a>XML 名称  
 XML 名称常常是导致 XML 编程复杂性的原因。 XML 名称由 XML 命名空间（也称为 XML 命名空间 URI）和本地名称组成。 XML 命名空间类似于基于 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 的程序中的命名空间。 它能够唯一限定元素和属性的名称。 这有助于避免 XML 文档各个部分之间的名称冲突。 声明 XML 命名空间后，可以选择只需在此命名空间内唯一的本地名称。  
  
 XML 名称的另一个方面是 XML 命名空间前缀。 XML 名称的复杂性大都是由 XML 前缀引起的。 这些前缀可用来创建 XML 命名空间的快捷方式，从而使 XML 文档更加简洁易懂。 但是，XML 前缀仅在其上下文中才有意义，这就增加了复杂性。 例如，XML 前缀 `aw` 可以与 XML 树的一部分中的一个 XML 命名空间关联，也可以与该 XML 树的另一部分中的另一个 XML 命名空间关联。  
  
 如果通过 Visual Basic 和 XML 文本使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，则在命名空间中处理文档时必须使用命名空间前缀。  
  
 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，表示 XML 名称的类为 <xref:System.Xml.Linq.XName>。 XML 名称在整个 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API 中频繁出现，任何时候只要需要 XML 名称，您就会发现 <xref:System.Xml.Linq.XName> 参数。 但是，很少会直接使用 <xref:System.Xml.Linq.XName>。 <xref:System.Xml.Linq.XName> 包含一个从字符串的隐式转换。  
  
 有关详细信息，请参阅 <xref:System.Xml.Linq.XNamespace> 和 <xref:System.Xml.Linq.XName>。  
  
## <a name="see-also"></a>请参阅

- [使用 XML 命名空间 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
