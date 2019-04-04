---
title: 如何：将 XML 转换通过使用 LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 0d07c47e64b7eaea80155eabbc50bc2bae0a889c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834252"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>如何：将 XML 转换通过使用 LINQ (Visual Basic)
[XML 文本](../../../../visual-basic/language-reference/xml-literals/index.md)轻松地从一个源中读取 XML 并将其转换为新的 XML 格式。 您可以充分利用 LINQ 查询以检索要转换的内容或将现有文档中的内容更改为新的 XML 格式。  
  
 本主题中的示例转换为 HTML，以在浏览器中查看 XML 源文档中的内容。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>若要将 XML 文档转换  
  
1.  在 Visual Studio 中创建新的 Visual Basic 项目中**控制台应用程序**项目模板。  
  
2.  双击要修改的 Visual Basic 代码的项目中创建的 Module1.vb 文件。 将以下代码添加到`Sub Main`的`Module1`模块。 此代码将创建源 XML 文档作为<xref:System.Xml.Linq.XDocument>对象。  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [如何：从文件、 字符串或 Stream 加载 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。  
  
3.  若要创建源 XML 文档的代码后, 添加以下代码以检索所有\<书籍 > 对象中的元素并将它们转换为 HTML 文档。 列表\<书籍 > 元素通过使用 LINQ 查询返回的集合创建<xref:System.Xml.Linq.XElement>包含转换后的 HTML 的对象。 嵌入的表达式可用于将源文档中新的 XML 格式的值。  
  
     生成的 HTML 文档通过使用写入到文件<xref:System.Xml.Linq.XElement.Save%2A>方法。  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  之后`Sub Main`的`Module1`，添加一个新方法 (`Sub`) 来转换\<说明 > 为指定的 HTML 格式的节点。 此方法称为由上一步中的代码，用于保留的格式\<说明 > 元素。  
  
     此方法将替换的子元素\<说明 > 具有 HTML 元素。 `ReplaceWith`方法用于保留的子元素的位置。 转换后的内容\<说明 > 元素包含在 HTML 段落 (\<p >) 元素。 <xref:System.Xml.Linq.XContainer.Nodes%2A>属性用于检索转换后的内容\<说明 > 元素。 这可确保在转换后的内容中包含子元素。  
  
     添加以下代码后的`Sub Main`的`Module1`。  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  保存更改。  
  
6.  按 F5 以运行代码。 产生的保存的文档将如下所示：  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>请参阅

- [XML 文本](../../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中操控 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [如何：从文件、 字符串或 Stream 加载 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
