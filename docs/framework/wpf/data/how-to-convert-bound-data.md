---
title: 如何：转换已绑定的数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093795"
---
# <a name="how-to-convert-bound-data"></a>如何：转换已绑定的数据
此示例演示如何将应用到绑定中使用的数据转换。  
  
 若要在绑定期间转换数据，必须创建一个类以实现 <xref:System.Windows.Data.IValueConverter> 接口，其中包括 <xref:System.Windows.Data.IValueConverter.Convert%2A> 和 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方法。  
  
## <a name="example"></a>示例  
 下面的示例演示了一个日期转换器的实现，该转换器将转换传入的日期值，使其仅显示年、月、日。 实现 <xref:System.Windows.Data.IValueConverter> 接口时，使用 <xref:System.Windows.Data.ValueConversionAttribute> 属性修饰该实现以向开发工具表明转换中涉及的数据类型，这是一个非常好的做法，如以下示例所示：  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 创建一个转换器后，可以将其添加为中的资源在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]文件。 在以下示例中， *src*映射到在其中命名空间*DateConverter*定义。  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最后，您可以使用以下语法在绑定中使用转换器。 在下面的示例中，文本的内容<xref:System.Windows.Controls.TextBlock>绑定到*StartDate*，这是外部数据源属性。  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上面的示例引用的样式资源在一个未在此主题中列出的资源部分中定义。  
  
## <a name="see-also"></a>请参阅

- [实现绑定验证](how-to-implement-binding-validation.md)
- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
