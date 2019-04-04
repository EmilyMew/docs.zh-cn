---
title: Imports 语句-XML Namespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 97d08113a37477add9d770b0a680c303fe7e3040
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841402"
---
# <a name="imports-statement-xml-namespace"></a>Imports 语句（XML 命名空间）
导入在 XML 文本和 XML 轴属性中使用的 XML 命名空间前缀。  
  
## <a name="syntax"></a>语法  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>部件  
 `xmlNamespacePrefix`  
 可选。 由哪些 XML 元素和属性可以引用的字符串`xmlNamespaceName`。 如果没有`xmlNamespacePrefix`是提供，导入的 XML 命名空间是默认 XML 命名空间。 必须是有效的 XML 标识符。 有关详细信息，请参阅[名称的声明 XML 元素和属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。  
  
 `xmlNamespaceName`  
 必需。 标识要导入的 XML 命名空间的字符串。  
  
## <a name="remarks"></a>备注  
 可以使用`Imports`语句来定义与 XML 文本和 XML 轴属性，或作为参数传递到可以使用的全局 XML 命名空间`GetXmlNamespace`运算符。 (有关使用信息`Imports`语句导入别名，可在代码中，使用类型名称，请参阅[Imports 语句 （.NET Namespace 和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。)通过使用声明 XML 命名空间的语法`Imports`语句等同于在 XML 中使用的语法。 因此，您可以从 XML 文件中复制的命名空间声明，并使用它在`Imports`语句。  
  
 你想要反复创建相同的命名空间中的 XML 元素时，XML 命名空间前缀非常有用。 使用 XML 命名空间前缀声明`Imports`语句是全局的意义上说，它是适用于所有代码文件中。 在创建 XML 元素文本和 XML 轴属性的访问时，可以使用它。 有关详细信息，请参阅[XML 元素文本](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)并[XML 轴属性](../../../visual-basic/language-reference/xml-axis/index.md)。  
  
 如果定义一个不带命名空间前缀的全局 XML 命名空间 (例如， `Imports <xmlns="http://SomeNameSpace>"`)，该命名空间被视为默认 XML 命名空间。 默认 XML 命名空间用于任何 XML 元素文本或 XML 特性轴属性的未显式指定命名空间。 如果指定的命名空间是空的命名空间还使用默认命名空间 (即， `xmlns=""`)。 默认 XML 命名空间不适用于 XML 文本中的 XML 特性或不具有命名空间的 XML 特性轴属性。  
  
 XML 定义的命名空间中 XML 文本，也称为*本地 XML 命名空间*，通过定义的 XML 命名空间的优先级高于`Imports`语句作为全局。 由定义的 XML 命名空间`Imports`语句优先于为 Visual Basic 项目导入的 XML 命名空间。 如果 XML 文本定义的 XML 命名空间，该本地命名空间不适用于嵌入的表达式。  
  
 全局 XML 命名空间按照与.NET Framework 命名空间相同的作用域和定义规则。 因此，可以包括`Imports`语句来定义一个全局的 XML 命名空间可以在任意位置导入.NET Framework 命名空间。 这包括代码文件和项目级别导入命名空间。 有关项目级别导入命名空间的信息，请参阅[引用页上，项目设计器 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。  
  
 每个源文件可以包含任意数量的`Imports`语句。 这些必须遵循选项声明，如`Option Strict`语句，并且它们必须位于之前编程元素声明，如`Module`或`Class`语句。  
  
## <a name="example"></a>示例  
 下面的示例将默认 XML 命名空间和 XML 命名空间前缀标识导入`ns`。 然后，创建使用这两个命名空间的 XML 文本。  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
 此代码显示以下文本：  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>示例  
 以下示例将导入的 XML 命名空间前缀`ns`。 然后，创建 XML 文本的使用的命名空间前缀，并显示元素的最终形式。  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 此代码显示以下文本：  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 请注意，编译器为本地前缀定义从全局前缀转换的 XML 命名空间前缀。  
  
## <a name="example"></a>示例  
 以下示例将导入的 XML 命名空间前缀`ns`。 然后它使用该命名空间前缀来创建 XML 文本并访问具有限定名称 `ns:name` 的第一个子节点。  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 此代码显示以下文本：  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>请参阅

- [XML 元素文本](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 轴属性](../../../visual-basic/language-reference/xml-axis/index.md)
- [已声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace 运算符](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
