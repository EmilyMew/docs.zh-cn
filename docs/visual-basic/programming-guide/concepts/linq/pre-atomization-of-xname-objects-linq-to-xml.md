---
title: XName 对象 (LINQ to XML) 的预原子化 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819289"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>XName 对象 (LINQ to XML) 的预原子化 (Visual Basic)
提高 LINQ to XML 中的性能的一种方法是预原子化 <xref:System.Xml.Linq.XName> 对象。 预原子化是指在通过使用 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XElement> 类的构造函数创建 XML 树之前，先将字符串分配给 <xref:System.Xml.Linq.XAttribute> 对象。 然后传递初始化的 <xref:System.Xml.Linq.XName> 对象，而不是将字符串传递给构造函数（此过程将使用从字符串到 <xref:System.Xml.Linq.XName> 的隐式转换）。  
  
 当创建其中重复出现特定名称的大型 XML 树时，这样可以提高性能。 为此，请在构造 XML 树之前声明和初始化 <xref:System.Xml.Linq.XName> 对象，然后使用 <xref:System.Xml.Linq.XName> 对象，而不是指定元素和属性名称的字符串。 当创建大量具有相同名称的元素（或属性）时，此技术可以显著提高性能。  
  
 应针对您的方案测试预原子化以确定是否应使用它。  
  
## <a name="example"></a>示例  
 下面的示例演示这一操作。  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 下面的示例演示针对命名空间中的 XML 文档的相同技术：  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 下面的示例更类似于实际中可能遇到的情况。 在此示例中，元素的内容由查询提供：  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 上一示例的执行性能优于下面的示例（其中未对名称进行预原子化）：  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>请参阅

- [性能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [原子化的 XName 和 XNamespace 对象 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
