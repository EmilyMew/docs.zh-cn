---
title: 如何：使用 DataGrid 控件实现验证
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: aead8cbd500262a4cba535fd023dd9701d50257a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086801"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>如何：使用 DataGrid 控件实现验证
<xref:System.Windows.Controls.DataGrid>控件，可以在单元格和行级别执行验证。 与单元格级别验证时用户更新的值验证绑定的数据对象的各个属性。 使用行级验证时用户将更改提交到行验证整个数据对象。 此外可以为验证错误，提供自定义可视反馈，或使用默认的可视反馈的<xref:System.Windows.Controls.DataGrid>控件提供。  
  
 下面的过程介绍如何将应用到的验证规则<xref:System.Windows.Controls.DataGrid>绑定和自定义可视反馈。  
  
### <a name="to-validate-individual-cell-values"></a>若要验证单个单元格的值  
  
-   指定的列使用绑定上的一个或多个验证规则。 这是类似于验证简单控件中的数据，如中所述[数据绑定概述](../data/data-binding-overview.md)。  
  
     下面的示例演示<xref:System.Windows.Controls.DataGrid>具有四个列绑定到业务对象的不同属性的控件。 三个列指定<xref:System.Windows.Controls.ExceptionValidationRule>通过设置<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>属性设置为`true`。  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     当用户输入无效值 （如非整数中的课程 ID 列） 时，在单元格周围将出现一个红色边框。 您可以更改此默认验证反馈，如下面的过程中所述。  
  
### <a name="to-customize-cell-validation-feedback"></a>若要自定义单元格验证反馈  
  
-   设置列的<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>属性设置为一种样式适用于列的编辑控件。 由于在运行时创建编辑控件，不能使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>附加属性，就像对简单控件。  
  
     下面的示例通过添加由验证规则的三个列共享了错误样式更新前面的示例。 当用户输入的值无效时，样式更改单元格背景色，添加工具提示。 请注意，使用的触发器，以确定是否存在验证错误。 这是必需的因为当前单元格没有专用的错误模板。  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     您可以通过替换来实现更广泛的自定义<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>列使用。  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>若要验证单个行中的多个值  
  
1.  实现<xref:System.Windows.Controls.ValidationRule>检查多个属性的绑定的数据对象的子类。 在你<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法实现转换`value`参数值到<xref:System.Windows.Data.BindingGroup>实例。 然后可以访问通过此数据对象<xref:System.Windows.Data.BindingGroup.Items%2A>属性。  
  
     下面的示例展示了此过程来验证是否`StartDate`属性值`Course`对象是早于其`EndDate`属性值。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  添加验证规则与<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合。 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>属性提供直接访问权限<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>属性的<xref:System.Windows.Data.BindingGroup>分组控件使用的所有绑定的实例。  
  
     下面的示例设置<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>在 XAML 中的属性。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>属性设置为<xref:System.Windows.Controls.ValidationStep.UpdatedValue>，以便仅在绑定的数据对象更新后进行的验证。  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     当用户指定结束日期早于开始日期时，行标题中会显示一个红色感叹号 （！）。 您可以更改此默认验证反馈，如下面的过程中所述。  
  
### <a name="to-customize-row-validation-feedback"></a>若要自定义行验证反馈  
  
-   设置 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 属性。 此属性可以自定义为各个行验证反馈<xref:System.Windows.Controls.DataGrid>控件。 您也可以通过使用隐式行样式设置影响多个控件<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>属性。  
  
     下面的示例使用一个更可见的指示符替换默认行验证反馈。 当用户输入的值无效时，一个带有白色感叹号红色圆圈显示在行标题中。 这是个行和单元格的验证错误。 工具提示中显示相关联的错误消息。  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>示例  
 下面的示例提供了单元格和行验证的完整演示。 `Course`类提供了实现的示例数据对象<xref:System.ComponentModel.IEditableObject>以支持事务。 <xref:System.Windows.Controls.DataGrid>控件与交互<xref:System.ComponentModel.IEditableObject>以使用户能够通过按 esc 键还原更改。  
  
> [!NOTE]
>  如果使用的 Visual Basic 中，在 MainWindow.xaml 的第一行中，替换`x:Class="DataGridValidation.MainWindow"`与`x:Class="MainWindow"`。  
  
 若要测试验证，请尝试以下操作：  
  
-   在课程 ID 列中，输入一个非整数值。  
  
-   在结束日期列中，输入日期早于开始日期。  
  
-   删除课程 ID、 开始日期或结束日期中的值。  
  
-   若要撤消了无效的单元值，请将光标放回该单元格，然后按 ESC 键。  
  
-   若要撤消整个行的更改，当前单元格处于编辑模式时，请按 ESC 键两次。  
  
-   出现验证错误时，将鼠标指针移动行标题以查看相关联的错误消息中的指示符。  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [数据绑定](../data/data-binding-wpf.md)
- [实现绑定验证](../data/how-to-implement-binding-validation.md)
- [在自定义对象上实现验证逻辑](../data/how-to-implement-validation-logic-on-custom-objects.md)
