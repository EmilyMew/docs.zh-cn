---
title: 扩展索引器属性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a02c482db81d9d76752cfe66a292dc57c48b2acb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841239"
---
# <a name="extension-indexer-property-visual-basic"></a>扩展索引器属性 (Visual Basic)
提供对集合中各个元素的访问。  
  
## <a name="syntax"></a>语法  
  
```  
object(index)  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`object`|必需。 可查询的集合。 也就是说，集合实现<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。|  
|(|必需。 表示索引器属性的开头。|  
|`index`|必需。 一个整数表达式，指定集合的元素的从零开始的位置。|  
|)|必需。 表示索引器属性的结尾。|  
  
## <a name="return-value"></a>返回值  
 从集合中指定的位置的对象或`Nothing`如果索引超出范围。  
  
## <a name="remarks"></a>备注  
 扩展索引器属性可用于访问集合中的各个元素。 XML 轴属性的输出通常使用此索引器属性。 XML 子和 XML 子代轴属性返回的集合<xref:System.Xml.Linq.XElement>对象或属性值。  
  
 Visual Basic 编译器将扩展索引器属性转换为对调用`ElementAtOrDefault`方法。 与数组索引器，不同`ElementAtOrDefault`方法将返回`Nothing`如果索引超出范围。 此行为时，你无法轻松确定集合中的元素数。  
  
 此索引器属性是为实现的集合的扩展属性相似<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>： 仅当集合不具有索引器或默认属性使用它。  
  
 若要访问的集合中的第一个元素的值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>对象，可以使用 XML`Value`属性。 有关详细信息，请参阅[XML 值属性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用扩展索引器访问的集合中的第二个子节点<xref:System.Xml.Linq.XElement>对象。 通过使用子轴属性，它将获取名为的所有子元素访问集合`phone`在`contact`对象。  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 此代码显示以下文本：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- [XML 轴属性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 值属性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
