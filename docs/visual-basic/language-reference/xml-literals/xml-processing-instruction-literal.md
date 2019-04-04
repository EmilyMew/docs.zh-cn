---
title: XML 处理指令文本 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3fbb16a4d47801b671d37566573215d3a57afff1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820147"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 处理指令文本 (Visual Basic)
一个文本表示<xref:System.Xml.Linq.XProcessingInstruction>对象。  
  
## <a name="syntax"></a>语法  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>部件  
 `<?`  
 必需。 表示 XML 处理指令文本的开头。  
  
 `piName`  
 必需。 命名，该值指示哪个应用程序的处理指令目标。 不能以"xml"或"XML"开头。  
  
 `piData`  
 可选。 指示应用程序的目标字符串`piName`应处理 XML 文档。  
  
 `?>`  
 必需。 表示处理指令的结尾。  
  
## <a name="return-value"></a>返回值  
 一个 <xref:System.Xml.Linq.XProcessingInstruction> 对象。  
  
## <a name="remarks"></a>备注  
 XML 处理指令文本指示应用程序应如何处理 XML 文档。 在应用程序加载 XML 文档时，应用程序可以检查 XML 处理指令，以确定如何处理文档。 应用程序要解释的含义`piName`和`piData`。  
  
 XML 文档文本使用类似于 XML 处理指令的语法。 有关详细信息，请参阅[XML 文档文本](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
> [!NOTE]
>  `piName`元素不能以开头的字符串"xml"或"XML"，因为 XML 1.0 规范保留了这些标识符。  
  
 可以将 XML 处理指令文本分配给一个变量，或将其包含在 XML 文档文本。  
  
> [!NOTE]
>  XML 文本可以跨多个行，而无需行继续符。 这使您可以从 XML 文档中复制内容并将其粘贴到 Visual Basic 程序直接。  
  
 Visual Basic 编译器将 XML 处理指令文本转换为调用<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>构造函数。  
  
## <a name="example"></a>示例  
 以下示例创建标识 XML 文档的样式表的处理指令。  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XProcessingInstruction>
- [XML 文档文本](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 文本](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中创建 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
