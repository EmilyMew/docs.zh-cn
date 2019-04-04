---
title: XML 值属性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 1c7aa1cc32bc1c5ef637f7a606db7e695f1dfaee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821944"
---
# <a name="xml-value-property-visual-basic"></a>XML 值属性 (Visual Basic)
提供对一系列的第一个元素的值的访问<xref:System.Xml.Linq.XElement>对象。  
  
## <a name="syntax"></a>语法  
  
```  
object.Value  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`object`|必需。 <xref:System.Xml.Linq.XElement> 对象的集合。|  
  
## <a name="return-value"></a>返回值  
 一个`String`包含值的集合的第一个元素或`Nothing`集合是否为空。  
  
## <a name="remarks"></a>备注  
 <xref:System.Xml.Linq.XElement.Value%2A>属性，则可以轻松访问的集合中的第一个元素的值<xref:System.Xml.Linq.XElement>对象。 此属性首先检查集合是否包含至少一个对象。 如果集合为空，此属性返回`Nothing`。 否则，此属性返回的值<xref:System.Xml.Linq.XElement.Value%2A>集合中的第一个元素的属性。  
  
> [!NOTE]
>  当访问的 XML 属性使用值\@的标识符，则返回属性值为`String`并不需要显式指定<xref:System.Xml.Linq.XAttribute.Value%2A>属性。  
  
 若要访问集合中的其他元素，可以使用 XML 扩展索引器属性。 有关详细信息，请参阅[扩展索引器属性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)。  
  
## <a name="inheritance"></a>继承  
 大多数用户不需要实现<xref:System.Collections.Generic.IEnumerable%601>，因此可以忽略本部分中。  
  
 <xref:System.Xml.Linq.XElement.Value%2A>属性是扩展属性的类型的实现`IEnumerable(Of XElement)`。 此扩展属性的绑定是类似的扩展方法绑定： 如果某个类型实现一个接口，并且定义了一个具有名称"值"的属性，该属性的优先级高于该扩展属性。 换而言之，这<xref:System.Xml.Linq.XElement.Value%2A>可以通过定义一个新的属性实现的类中重写属性`IEnumerable(Of XElement)`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用<xref:System.Xml.Linq.XElement.Value%2A>属性来访问的集合中的第一个节点<xref:System.Xml.Linq.XElement>对象。 该示例使用子轴属性来获取名为的所有子节点的集合`phone`位于`contact`对象。  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 此代码显示以下文本：  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取集合中的 XML 特性的值<xref:System.Xml.Linq.XAttribute>对象。 该示例使用特性轴属性来显示的值`type`的所有属性`phone`元素。  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 此代码显示以下文本：  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML 轴属性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [扩展方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [扩展索引器属性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [XML 子轴属性](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 特性轴属性](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
