---
title: 如何：使用 FontSizeConverter 类
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088179"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>如何：使用 FontSizeConverter 类
## <a name="example"></a>示例  
 此示例演示如何创建的实例<xref:System.Windows.FontSizeConverter>并使用它来更改字体大小。  
  
 该示例定义一个名为的自定义方法`changeSize`的内容的转换<xref:System.Windows.Controls.ListBoxItem>在单独的定义，[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的实例的文件， <xref:System.Double>，然后再转换<xref:System.String>。 此方法将传递<xref:System.Windows.Controls.ListBoxItem>到<xref:System.Windows.FontSizeConverter>对象，它将转换<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的实例<xref:System.Double>。 然后将此值传递的值为<xref:System.Windows.Controls.TextBlock.FontSize%2A>属性的<xref:System.Windows.Controls.TextBlock>元素。  
  
 此示例还定义调用的第二个自定义方法`changeFamily`。 此方法将转换<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>到<xref:System.String>，然后将传递到该值<xref:System.Windows.Controls.TextBlock.FontFamily%2A>属性<xref:System.Windows.Controls.TextBlock>元素。  
  
 此示例不运行。  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FontSizeConverter>
