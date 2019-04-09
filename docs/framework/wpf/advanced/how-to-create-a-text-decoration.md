---
title: 如何：创建文本修饰
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133830"
---
# <a name="how-to-create-a-text-decoration"></a>如何：创建文本修饰
一个<xref:System.Windows.TextDecoration>对象是可以添加到文本的视觉装饰。 有四种类型的文本修饰： 下划线、 基线、 删除线和上划线。 下面的示例显示了文本修饰相对于文本的位置。  
  
 ![文本修饰类型的关系图](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 若要将文本修饰添加到文本中，创建<xref:System.Windows.TextDecoration>对象，并修改其属性。 使用<xref:System.Windows.TextDecoration.Location%2A>属性来指定文本修饰的显示位置，如下划线。 使用<xref:System.Windows.TextDecoration.Pen%2A>属性来指定文本修饰，如纯色填充或渐变颜色的外观。 如果未指定的值<xref:System.Windows.TextDecoration.Pen%2A>属性，为相同的颜色为文本修饰默认值。 定义后<xref:System.Windows.TextDecoration>对象，将其添加到<xref:System.Windows.TextDecorations>所需的文本对象的集合。  
  
 下面的示例演示了样式使用线性渐变画笔和虚线的笔的文本修饰。  
  
 ![采用线性渐变下划线的文本修饰](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <xref:System.Windows.Documents.Hyperlink>对象是允许您承载流内容中的超链接的内联级流内容元素。 默认情况下<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>对象来显示下划线。 <xref:System.Windows.TextDecoration> 对象可以是占用实例化，特别是当有许多<xref:System.Windows.Documents.Hyperlink>对象。 如果充分利用了<xref:System.Windows.Documents.Hyperlink>元素，您可能会考虑显示下划线，仅当触发事件，如<xref:System.Windows.ContentElement.MouseEnter>事件。  
  
 在以下示例中，"我的 MSN"链接的下划线是动态的 — 它时，才显示<xref:System.Windows.ContentElement.MouseEnter>触发事件。  
  
 ![显示 TextDecoration 的超链接](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 有关详细信息，请参阅[指定是否为超链接添加下划线](how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
## <a name="example"></a>示例  
 在下面的代码示例中，下划线文本修饰使用的默认字体值。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 下面的代码示例，笔纯色画笔创建下划线文本修饰。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 以下代码示例中，虚线笔线性渐变画笔创建下划线文本修饰。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [指定是否为超链接添加下划线](how-to-specify-whether-a-hyperlink-is-underlined.md)
