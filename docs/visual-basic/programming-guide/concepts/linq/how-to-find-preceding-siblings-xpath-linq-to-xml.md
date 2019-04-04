---
title: 如何：查找前面的同级 (XPATH-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
ms.openlocfilehash: 4584a84df0e25b451a440c33e17c14cd78fc78bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833004"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a>如何：查找前面的同级 (XPATH-LINQ to XML) (Visual Basic)
本主题将 XPath `preceding-sibling` 轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 子 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 轴进行比较。  
  
 XPath 表达式为：  
  
 `preceding-sibling::*`  
  
 请注意，<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 和 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 的结果都遵循文档顺序。  
  
## <a name="example"></a>示例  
 下面的示例查找 `FullAddress` 元素，然后使用 `preceding-sibling` 轴检索前面的元素。  
  
 此示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 该示例产生下面的输出：  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 针对 XPath 用户 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
