---
title: 如何：查找子元素 (XPATH-LINQ to XML) 的后代 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: 178729640898556244657e6e2917373825a4e51e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819003"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a>如何：查找子元素 (XPATH-LINQ to XML) 的后代 (Visual Basic)
本主题演示如何获取具有特定名称的子元素的后代元素。  
  
 XPath 表达式为：  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>示例  
 本示例模拟从文字处理文档的 XML 表示形式中提取文本的问题。 示例首先选择所有 `Paragraph` 元素，然后选择每个 `Text` 元素的所有 `Paragraph` 后代元素。 它不选择 `Text` 元素的后代 `Comment` 元素。  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Paragraph>  
            <Text>This is the start of</Text>  
        </Paragraph>  
        <Comment>  
            <Text>This comment is not part of the paragraph text.</Text>  
        </Comment>  
        <Paragraph>  
            <Annotation Emphasis='true'>  
                <Text> a sentence.</Text>  
            </Annotation>  
        </Paragraph>  
        <Paragraph>  
            <Text>  This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 该示例产生下面的输出：  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 针对 XPath 用户 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
