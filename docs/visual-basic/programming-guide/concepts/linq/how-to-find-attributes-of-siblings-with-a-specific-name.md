---
title: 如何：查找具有特定名称 (XPATH-LINQ to XML) 的同级属性 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 07fb5647950c450d08ab3235ac8cb396eff15305
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839049"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a>如何：查找具有特定名称 (XPATH-LINQ to XML) 的同级属性 (Visual Basic)
本主题演示如何查找上下文节点的同级的所有属性。 只返回集合中具有特定名称的属性。  
  
 XPath 表达式为：  
  
 `../Book/@id`  
  
## <a name="example"></a>示例  
 本示例首先查找 `Book` 元素，然后查找名为 `Book` 的所有同级元素，再查找名为 `id` 的所有属性。 结果是一个属性集合。  
  
 此示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 该示例产生下面的输出：  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 针对 XPath 用户 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
