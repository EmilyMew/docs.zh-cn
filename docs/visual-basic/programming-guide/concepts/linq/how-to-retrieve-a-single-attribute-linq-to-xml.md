---
title: 如何：检索单个特性 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: f56bdf86e4b63bc952c1d139aac9ee619b5a5f6c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837120"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>如何：检索单个特性 (LINQ to XML) (Visual Basic)
本主题说明在给定属性名称的情况下，如何检索元素的单个属性。 这对于编写查询表达式查找具有特定属性的元素十分有用。  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A> 类的 <xref:System.Xml.Linq.XElement> 方法返回具有指定名称的 <xref:System.Xml.Linq.XAttribute>。  
  
## <a name="example"></a>示例  
 下面的示例使用 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法。  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 本示例首先在名为 `Phone` 的树中查找所有后代，然后查找名为 `type` 的属性。  
  
 此代码生成以下输出：  
  
```  
home  
work  
```  
  
## <a name="example"></a>示例  
 如果希望检索属性的值，可以强制转换该值，就像使用 <xref:System.Xml.Linq.XElement> 对象时一样。 下面的示例演示这一操作。  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 此代码生成以下输出：  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 为 <xref:System.Xml.Linq.XAttribute> 类提供了以下类型的显式强制转换运算符：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。  
  
## <a name="example"></a>示例  
 下面的示例显式命名空间中的属性的相同代码。 有关详细信息，请参阅[使用 XML 命名空间 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 此代码生成以下输出：  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 轴 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
