---
title: 如何：绑定到方法
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 6cdad46fd6d9ef3bc4ce1a13fedb6ff1d639d93e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123235"
---
# <a name="how-to-bind-to-a-method"></a>如何：绑定到方法
下面的示例演示如何将绑定到方法使用<xref:System.Windows.Data.ObjectDataProvider>。  
  
## <a name="example"></a>示例  
 在本示例中，`TemperatureScale` 是一个具有 `ConvertTemp` 方法的类，该方法接收两个参数（分别为 `double` 和 `enum` 类型的 `TempType)`），将给定值从一个温标转换为另一个温标。 在以下示例中，<xref:System.Windows.Data.ObjectDataProvider> 用来实例化 `TemperatureScale` 对象。 将使用两个指定参数调用 `ConvertTemp` 方法。  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 现在此方法可以作为资源使用，因此可绑定到其结果。 在以下示例中，<xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.TextBox.Text%2A> 属性和 <xref:System.Windows.Controls.ComboBox> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 绑定到该方法的两个参数。 这样用户就可以指定要转换的温度以及要从哪个温标进行转换。 注意，<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 设置为 `true` 是因为我们要绑定到 <xref:System.Windows.Data.ObjectDataProvider> 实例的 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 属性，而不是由 <xref:System.Windows.Data.ObjectDataProvider> 包装的对象（`TemperatureScale`对象）的属性。  
  
 最后一个 <xref:System.Windows.Controls.Label> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 会在用户修改 <xref:System.Windows.Controls.TextBox> 的内容或 <xref:System.Windows.Controls.ComboBox> 的选项时更新。  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 `DoubleToString` 转换器在 <xref:System.Windows.Data.IValueConverter.Convert%2A> 方向接受一个双精度值并将其转换为字符串（从绑定源到绑定目标，后者为 <xref:System.Windows.Controls.TextBox.Text%2A> 属性），在<xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方向将 `string` 转换为 `double`。  
  
 `InvalidationCharacterRule` 是一个 <xref:System.Windows.Controls.ValidationRule>，用于检查无效字符。 当输入值不是一个 `double` 值时，默认错误模板（一个围绕 <xref:System.Windows.Controls.TextBox> 的红色边框）将出现，对用户进行通知。  
  
## <a name="see-also"></a>请参阅

- [帮助主题](data-binding-how-to-topics.md)
- [绑定到枚举](how-to-bind-to-an-enumeration.md)
