---
title: 如何：访问 XML 子代元素 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: bfbf849bd296f639f03580346e4a9c52ce000abd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832211"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>如何：访问 XML 子代元素 (Visual Basic)
此示例演示如何使用子代轴属性来访问具有指定的名称并且包含 XML 元素下的所有 XML 元素。 具体而言，它使用`Value`属性设置为集合中获取第一个元素的值`name`子代轴属性返回。 `name`子代轴属性获取名为的所有元素`name`中包含的`contacts`对象。 此示例还使用`phone`子代轴属性来访问名为的所有后代`phone`中包含的`contacts`对象。  
  
## <a name="example"></a>示例  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 <xref:System.Xml.Linq> 命名空间的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML 子代轴属性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML 值属性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中访问 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
