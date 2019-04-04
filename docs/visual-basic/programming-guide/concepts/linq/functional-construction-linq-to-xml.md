---
title: 功能构造 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816546"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>功能构造 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 为创建 XML 元素提供了一种称为“函数构造”的有效方式。 函数构造是指在单个语句中创建 XML 树的能力。  
  
 启用函数构造的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 编程接口有几个重要功能：  
  
-   <xref:System.Xml.Linq.XElement> 构造函数可以对内容采用多种类型的参数。 例如，可以传递另一个 <xref:System.Xml.Linq.XElement> 对象，该对象将成为一个子元素。 可以传递一个 <xref:System.Xml.Linq.XAttribute> 对象，该对象将成为该元素的一个属性。 也可以传递任何其他类型的对象，该对象将转换为字符串并成为该元素的文本内容。  
  
-   <xref:System.Xml.Linq.XElement> 函数采用类型为 `params` 的 <xref:System.Object> 数组，因此可以向该构造函数传递任意数目的对象。 这使您可以创建具有复杂内容的元素。  
  
-   如果对象实现 <xref:System.Collections.Generic.IEnumerable%601>，则枚举对象中的集合，并添加集合中的所有项。 如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 对象，则单独添加集合中的每一项。 这一功能很重要，因为它允许您将 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询的结果传递给构造函数。  
  
 下面是一个示例：  
  
 这些功能使您能够编写代码以创建 XML 树，以及编写使用的结果的代码使用 XML 文本[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询创建 XML 树时：  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>请参阅

- [创建 XML 树 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
