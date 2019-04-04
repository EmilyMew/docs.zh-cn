---
title: 如何：分析字符串 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: 815e94b3b41c2c0cc1d18d598307ab292919bea4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827297"
---
# <a name="how-to-parse-a-string-visual-basic"></a>如何：分析字符串 (Visual Basic)
本主题演示如何创建 XML 树中的C#。  
  
## <a name="example"></a>示例  
 可以通过分析在 Visual Basic 中的字符串`XElement.Parse`方法。 但是，它是使用 XML 文本中所示下面的代码，因为 XML 文本不会受到相同的性能损失，从字符串分析 XML 那样更加高效。  
  
 通过使用 XML 文本，可以只需复制并将 XML 粘贴到 Visual Basic 程序。  
  
> [!NOTE]
>  分析文本或从文本文件加载 XML 文档比函数构造的效率更低。 如果要从代码初始化 XML 树，使用函数构造比分析文本所占用的处理器时间更少。  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a>请参阅

- [分析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
