---
title: XML 注释文本 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 149bbac6d301a9c2f166d05698e3780171126cb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827271"
---
# <a name="xml-comment-literal-visual-basic"></a>XML 注释文本 (Visual Basic)
一个文本表示<xref:System.Xml.Linq.XComment>对象。  
  
## <a name="syntax"></a>语法  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`<!--`|必需。 表示 XML 注释的开始。|  
|`content`|必需。 XML 注释中显示的文本。 不能包含一系列的两个连字符 （-） 或与结束标记相邻的连字符结尾。|  
|`-->`|必需。 表示 XML 注释的结尾。|  
  
## <a name="return-value"></a>返回值  
 一个 <xref:System.Xml.Linq.XComment> 对象。  
  
## <a name="remarks"></a>备注  
 XML 注释文本不包含文档内容;它们包含有关文档的信息。 序列"-->"结尾的 XML 注释部分。 这意味着以下几点：  
  
-   因为嵌入的分隔符是有效的 XML 注释内容，不能在 XML 注释文本中使用嵌入式的表达式。  
  
-   XML 注释节无法嵌套，因为`content`不能包含值"-->"。  
  
 可以将 XML 注释文本分配给一个变量，或将其包含在 XML 元素文本中。  
  
> [!NOTE]
>  XML 文本可以跨多个行，而无需使用行继续符。 此功能，可将内容从 XML 文档复制并粘贴直接到 Visual Basic 程序。  
  
 Visual Basic 编译器将 XML 注释文本转换为调用<xref:System.Xml.Linq.XComment.%23ctor%2A>构造函数。  
  
## <a name="example"></a>示例  
 以下示例创建 XML 注释包含文本"这是一条注释"。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XComment>
- [XML 元素文本](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
