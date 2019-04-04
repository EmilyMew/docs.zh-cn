---
title: GetXmlNamespace 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 757ca54e5ba370bf2cc48bc70499e7b43ec96ef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834746"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 运算符 (Visual Basic)
获取<xref:System.Xml.Linq.XNamespace>对应于指定的 XML 命名空间前缀的对象。  
  
## <a name="syntax"></a>语法  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>部件  
 `xmlNamespacePrefix`  
 可选。 用于标识的 XML 命名空间前缀的字符串。 如果提供，此字符串必须是有效的 XML 标识符。 有关详细信息，请参阅[名称的声明 XML 元素和属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。 如果不指定任何前缀，则返回默认命名空间。 如果指定没有默认命名空间，则返回空命名空间。  
  
## <a name="return-value"></a>返回值  
 <xref:System.Xml.Linq.XNamespace>对应于 XML 命名空间前缀的对象。  
  
## <a name="remarks"></a>备注  
 `GetXmlNamespace`运算符获取<xref:System.Xml.Linq.XNamespace>对象，它对应于 XML 命名空间前缀`xmlNamespacePrefix`。  
  
 可以使用直接在 XML 文本和 XML 轴属性中的 XML 命名空间前缀。 但是，必须使用`GetXmlNamespace`运算符将转换为的命名空间前缀<xref:System.Xml.Linq.XNamespace>对象，然后可以在代码中使用它。 您可以将附加到的非限定的元素名称<xref:System.Xml.Linq.XNamespace>对象获取完全限定<xref:System.Xml.Linq.XName>对象的多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]方法需要。  
  
## <a name="example"></a>示例  
 以下示例将导入`ns`作为 XML 命名空间前缀。 然后，它使用的命名空间前缀来创建 XML 文本和访问具有限定的名称的第一个子节点`ns:phone`。 然后将传递到的子节点`ShowName`子例程，它构造限定的名称，方法是使用`GetXmlNamespace`运算符。 `ShowName`子例程然后将传递到的限定的名<xref:System.Xml.Linq.XNode.Ancestors%2A>方法以获取父`ns:contact`节点。  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 当您调用`TestGetXmlNamespace.RunSample()`，它将显示一个消息框，包含以下文本：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>请参阅

- [Imports 语句（XML 命名空间）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [在 Visual Basic 中访问 XML](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
