---
title: 如何：检测 TextBox 中的文本何时更改
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091143"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>如何：检测 TextBox 中的文本何时更改
此示例演示使用一种方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件来执行的方法时中的文本<xref:System.Windows.Controls.TextBox>控制已更改。  
  
 中的代码隐藏类[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>想要监视的更改，控制插入要每当调用的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件触发。  此方法必须具有匹配所需的签名<xref:System.Windows.Controls.TextChangedEventHandler>委托。  
  
 调用事件处理程序时的内容<xref:System.Windows.Controls.TextBox>由用户或以编程方式更改控制。  
  
 **注意：** 此事件，则会激发<xref:System.Windows.Controls.TextBox>创建并最初会填充文本控件。  
  
## <a name="example"></a>示例  
 在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，用于定义你<xref:System.Windows.Controls.TextBox>控件，指定<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>属性值相匹配的事件处理程序方法名称。  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>示例  
 中的代码隐藏类[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，其中包含<xref:System.Windows.Controls.TextBox>想要监视的更改，控制插入要每当调用的方法<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件触发。  此方法必须具有匹配所需的签名<xref:System.Windows.Controls.TextChangedEventHandler>委托。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 调用事件处理程序时的内容<xref:System.Windows.Controls.TextBox>由用户或以编程方式更改控制。  
  
 **注意：** 此事件，则会激发<xref:System.Windows.Controls.TextBox>创建并最初会填充文本控件。  
  
 注释  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox 概述](textbox-overview.md)
- [RichTextBox 概述](richtextbox-overview.md)
