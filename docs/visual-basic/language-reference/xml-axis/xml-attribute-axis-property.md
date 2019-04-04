---
title: XML 特性轴属性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: a7a93608d14bcbec316228b59467b23e9247e043
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828794"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 特性轴属性 (Visual Basic)
提供访问的属性的值<xref:System.Xml.Linq.XElement>对象或集合中的第一个元素<xref:System.Xml.Linq.XElement>对象。  
  
## <a name="syntax"></a>语法  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>部件  
 `object`  
 必需。 <xref:System.Xml.Linq.XElement>对象或一系列<xref:System.Xml.Linq.XElement>对象。  
  
 .@  
 必需。 表示特性轴属性的开头。  
  
 <  
 可选。 表示的属性的名称的开头时`attribute`不是在 Visual Basic 中是有效的标识符。  
  
 `attribute`  
 必需。 若要访问的窗体的属性的名称 [`prefix`:]`name`。  
  
|部件|描述|  
|----------|-----------------|  
|`prefix`|可选。 该属性的 XML 命名空间前缀。 必须是使用 `Imports` 语句定义的全局 XML 命名空间。|  
|`name`|必需。 本地属性名称。 请参阅[声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 可选。 表示属性的名称的末尾时`attribute`不是在 Visual Basic 中是有效的标识符。  
  
## <a name="return-value"></a>返回值  
 包含的值的字符串`attribute`。 如果属性名称不存在，`Nothing`返回。  
  
## <a name="remarks"></a>备注  
 可以使用 XML 特性轴属性从按名称访问的属性值<xref:System.Xml.Linq.XElement>对象或从集合中的第一个元素<xref:System.Xml.Linq.XElement>对象。 可以按名称，检索的属性值，也可以将新属性添加到元素中，通过指定新名称前面有 @ 标识符。  
  
 如果是指 XML 属性使用 @ 标识符，返回的属性值为一个字符串，并且不需要显式指定<xref:System.Xml.Linq.XAttribute.Value%2A>属性。  
  
 XML 特性的命名规则不同于 Visual Basic 标识符的命名规则。 若要访问 XML 特性都不是有效的 Visual Basic 标识符的名称，请将名称括在尖括号 (\<和 >)。  
  
## <a name="xml-namespaces"></a>XML 命名空间  
 中特性轴属性的名称可以使用通过使用全局声明的只有 XML 命名空间前缀`Imports`语句。 它不能使用在 XML 元素文本中局部声明的 XML 命名空间前缀。 有关详细信息，请参阅[Imports 语句 (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取名为 XML 属性的值`type`集合中的 XML 元素名为`phone`。  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 此代码显示以下文本：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建这两个 XML 元素的属性作为一部分的 XML，并动态通过将属性添加到的实例，以声明方式<xref:System.Xml.Linq.XElement>对象。 `type`属性以声明方式创建和`owner`动态创建属性。  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 此代码显示以下文本：  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>示例  
 下面的示例使用尖括号语法来获取名为 XML 特性的值`number-type`，这不是在 Visual Basic 中是有效的标识符。  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 此代码显示以下文本：  
  
 `Phone type: work`  
  
## <a name="example"></a>示例  
 下面的示例声明 `ns` 作为 XML 命名空间前缀。 然后，它使用的命名空间前缀来创建 XML 文本和访问具有限定名称的第一个子节点"`ns:name`"。  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 此代码显示以下文本：  
  
 `Phone type: home`  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement>
- [XML 轴属性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [已声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
