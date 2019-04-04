---
title: 将元素、 属性和节点添加到 XML 树 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 35d3bdb27342dd7a871778ad4749db4d6849bd60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814305"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>将元素、 属性和节点添加到 XML 树 (Visual Basic)
可以向现有的 XML 树中添加内容（包括元素、属性、注释、处理指令、文本和 CDATA）。  
  
## <a name="methods-for-adding-content"></a>添加内容的方法  
 下面的方法将子内容添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 中：  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|在 <xref:System.Xml.Linq.XContainer> 的子内容的末尾添加内容。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|在 <xref:System.Xml.Linq.XContainer> 的子内容的开头添加内容。|  
  
 下面的方法将内容添加为 <xref:System.Xml.Linq.XNode> 的同级节点。 向其中添加同级内容的最常见的节点是 <xref:System.Xml.Linq.XElement>，不过你也可以将有效的同级内容添加到其他类型的节点，例如 <xref:System.Xml.Linq.XText> 或 <xref:System.Xml.Linq.XComment>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|在 <xref:System.Xml.Linq.XNode> 后面添加内容。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|在 <xref:System.Xml.Linq.XNode> 前面添加内容。|  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例创建两个 XML 树，然后修改其中一个树。  
  
### <a name="code"></a>代码  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a>注释  
 此代码生成以下输出：  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>请参阅

- [修改 XML 树 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
