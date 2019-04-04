---
title: 如何：使用字典使用 LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: def00fcd356472825ebc4b9f5c306cf3547991e1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820758"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>如何：使用字典使用 LINQ to XML (Visual Basic)
通常需要将各种数据结构转换为 XML 和将 XML 转换回其他数据结构。 本主题通过 <xref:System.Collections.Generic.Dictionary%602> 和 XML 的相互转换演示这一常规方法的具体实现。  
  
## <a name="example"></a>示例  
 此示例使用嵌入式表达式中的 XML 文本和查询。 查询投影新<xref:System.Xml.Linq.XElement>对象，该对象然后成为的新内容`Root`<xref:System.Xml.Linq.XElement>对象。  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 此代码生成以下输出：  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>示例  
 下面的代码从 XML 创建一个字典。  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 此代码生成以下输出：  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>请参阅

- [投影和转换 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
