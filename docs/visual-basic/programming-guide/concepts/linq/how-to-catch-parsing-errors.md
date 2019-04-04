---
title: 如何：捕捉分析错误 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 1a5d01d4853a9fd0cc7f0a0e5071b394ab3f218b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829368"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>如何：捕捉分析错误 (Visual Basic)
本主题演示如何检测格式不正确或无效的 XML。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过使用 <xref:System.Xml.XmlReader> 实现。 如果将格式不正确或无效的 XML 传递给 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，则基础 <xref:System.Xml.XmlReader> 类将引发异常。 用于分析 XML 的各种方法（如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>）不会捕捉异常；应用程序可以捕捉异常。  
  
 请注意，如果使用 XML 文本，则无法获取分析错误。 Visual Basic 编译器将捕捉格式不正确或无效的 XML 错误。  
  
## <a name="example"></a>示例  
 下面的代码尝试分析无效的 XML：  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 运行此代码时，会引发以下异常：  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 有关 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 和 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 方法可能会引发的异常的更多信息，请参见 <xref:System.Xml.XmlReader> 文档。  
  
## <a name="see-also"></a>请参阅

- [分析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
