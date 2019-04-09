---
title: 如何：控制文本框文本更新源的时间
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 28c1e0e23247cfaf48343bf10bb79c4862623fb6
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055126"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>如何：控制文本框文本更新源的时间
本主题介绍如何使用 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性控制绑定源更新的时机。 本主题使用 <xref:System.Windows.Controls.TextBox> 控件作为示例。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.TextBox.Text%2A> 属性具有默认值<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>的值<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 这意味着应用程序是否已<xref:System.Windows.Controls.TextBox>与数据绑定<xref:System.Windows.Controls.TextBox>。<xref:System.Windows.Controls.TextBox.Text%2A> 属性中，您将键入的文本<xref:System.Windows.Controls.TextBox>不会更新源之前<xref:System.Windows.Controls.TextBox>失去焦点 (例如，当单击离开<xref:System.Windows.Controls.TextBox>)。  
  
 如果希望源在键入时更新，请将绑定的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 设置为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 在下面的示例中，突出显示的代码行表明 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBlock> 的 `Text` 属性绑定到相同的源属性。 <xref:System.Windows.Controls.TextBox> 绑定的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性设置为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 因此，<xref:System.Windows.Controls.TextBlock> 会在用户将文本输入到 <xref:System.Windows.Controls.TextBox> 时显示相同的文本（因为源发生了更改），如示例的以下屏幕截图所示：  
  
 ![简单数据绑定示例屏幕截图](./media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 如果有一个对话框或可供用户编辑的窗体，并且需要将源更新延迟到用户完成字段的编辑并单击“确定”的时候，则可将绑定的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值设置为 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>，如以下示例所示：  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 将 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值设置为 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> 时，源值只会在应用程序调用 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 方法时更改。 下面的示例演示如何为 `itemNameTextBox` 调用 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>：  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  可以对其他控件的属性使用相同的技巧，但请记住，其他大多数属性的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>。 有关详细信息，请参阅 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性页。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性用于处理源更新，因此仅适用于 <xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定。 为了使 <xref:System.Windows.Data.BindingMode.TwoWay> 和 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定生效，源对象需要提供属性更改通知。 有关详细信息，可以参阅本主题中引用的示例。 此外，也可以参阅[实现属性更改通知](how-to-implement-property-change-notification.md)。  
  
## <a name="see-also"></a>请参阅
- [帮助主题](data-binding-how-to-topics.md)
