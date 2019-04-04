---
title: 如何：查找具有特定子元素的元素 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 1b226f009776f397f73ab9ee7826484eb8869f28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827050"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>如何：查找具有特定子元素的元素 (Visual Basic)
本主题演示如何查找特定元素，该特定元素包含具有特定值的子元素。  
  
## <a name="example"></a>示例  
 示例查找 `Test` 元素，该元素包含具有值为“Examp2.EXE”的 `CommandLine` 子元素。  
  
 此示例使用下面的 XML 文档：[示例 XML 文件：测试配置 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)。  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 此代码生成以下输出：  
  
```  
0002  
0006  
```  
  
 请注意，此示例中使用[XML 子轴属性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)，则[XML 特性轴属性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)，并[XML 值属性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何对命名空间中的 XML 进行同样的查询。 有关详细信息，请参阅[使用 XML 命名空间 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 此示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的测试配置](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md)。  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 此代码生成以下输出：  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [基本查询 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [标准查询运算符概述 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投影运算 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
