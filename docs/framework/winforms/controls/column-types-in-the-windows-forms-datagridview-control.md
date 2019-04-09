---
title: Windows 窗体 DataGridView 控件中的列类型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: a33cf4cd865921c04ef10c7fccf3a67c3d22de73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115669"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的列类型
<xref:System.Windows.Forms.DataGridView>控件使用几种列类型来显示其信息，并使用户能够修改或添加信息。  
  
 当绑定<xref:System.Windows.Forms.DataGridView>控件，并设置<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>属性设置为`true`，列会自动生成使用相应绑定的数据源中包含的数据类型的默认列类型。  
  
 此外可以自己创建的任何列类的实例，并将其添加到返回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>属性。 可以创建用于为未绑定列，这些实例，或者您可以手动将它们绑定。 手动绑定的列非常有用，例如，如果想要自动生成的列的一种类型替换为另一种类型的列。  
  
 下表描述了可用于在中使用的各种列类<xref:System.Windows.Forms.DataGridView>控件。  
  
|类|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|与基于文本的值一起使用。 绑定到数字和字符串时，会自动生成。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|用于<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 绑定到这些类型的值时，会自动生成。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|用于显示图像。 绑定到字节数组时自动生成<xref:System.Drawing.Image>对象，或<xref:System.Drawing.Icon>对象。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|用于在单元中显示按钮。 在绑定时，不会自动生成。 通常用作未绑定的列。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|用于在单元中显示的下拉列表。 在绑定时，不会自动生成。 通常手动进行数据绑定。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|用于在单元中显示的链接。 在绑定时，不会自动生成。 通常手动进行数据绑定。|  
|自定义列类型|您可以通过继承来创建您自己的列类<xref:System.Windows.Forms.DataGridViewColumn>类或任何其派生的类提供自定义外观、 行为或承载的控件。 有关详细信息，请参阅[如何：通过扩展行为和外观自定义单元格和 Windows 窗体 DataGridView 控件中的列](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 以下各节中更详细地介绍了这些列类型。  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>是一种通用的列类型与数字、 字符串等基于文本的值一起使用。 在编辑模式下，<xref:System.Windows.Forms.TextBox>控件显示在活动单元格，使用户能够修改单元格的值。  
  
 单元格的值会自动转换为显示的字符串。 输入或由用户修改值自动进行分析以创建相应的数据类型的单元格值。 您可以通过处理来自定义这些转换<xref:System.Windows.Forms.DataGridView.CellFormatting>并<xref:System.Windows.Forms.DataGridView.CellParsing>的事件<xref:System.Windows.Forms.DataGridView>控件。  
  
 中指定的列的单元格值数据类型<xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A>的列的属性。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>用于<xref:System.Boolean>和<xref:System.Windows.Forms.CheckState>值。 <xref:System.Boolean> 值显示为两个或三态复选框，具体取决于值<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>属性。 当列绑定到<xref:System.Windows.Forms.CheckState>值，<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>属性值是`true`默认情况下。  
  
 通常情况下，复选框单元格的值被合适的存储，如任何其他数据，或用于执行批量操作。 如果你想要立即当用户单击复选框单元格，可以处理响应<xref:System.Windows.Forms.DataGridView.CellClick>事件，但此事件发生之前更新单元格的值。 如果在单击时需要的新值，一种方法是计算所需的值将根据当前值。 另一种方法是立即提交更改并处理<xref:System.Windows.Forms.DataGridView.CellValueChanged>事件以对其做出响应。 若要提交更改，单击该单元格时，你必须处理<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>事件。 在处理程序中，如果当前单元格是一个复选框单元格，则调用<xref:System.Windows.Forms.DataGridView.CommitEdit%2A>方法并传入<xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>值。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn>用于显示图像。 Image 列可以从数据源将自动填充、 手动填充对于未绑定列，或处理程序中动态填充<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。  
  
 自动填充数据源的图像列的工作原理的不同的图像格式，包括支持的所有格式的字节数组<xref:System.Drawing.Image>类，并使用 Microsoft® Access 和 Northwind 示例数据库的 OLE 图片格式。  
  
 手动填充图像列时，你想要提供的功能<xref:System.Windows.Forms.DataGridViewButtonColumn>，但与自定义外观。 您可以处理<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>要响应图像单元格中的单击事件。  
  
 填充的处理程序中的图像列的单元格<xref:System.Windows.Forms.DataGridView.CellFormatting>事件非常有用，当你想要为计算出的值或非图像格式的值提供映像。 例如，可能会如具有字符串值的"风险"列`"high"`， `"middle"`，和`"low"`想要以图标形式显示。 或者，您可能包含必须加载而不是二进制内容的图像的图像的位置的"映像"列。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 使用<xref:System.Windows.Forms.DataGridViewButtonColumn>，可以显示包含按钮的单元格的列。 当您想要提供用于轻松对用户执行操作的特定记录，例如订购或在单独的窗口中显示子记录，这很有用。  
  
 数据绑定时，不会自动生成按钮列<xref:System.Windows.Forms.DataGridView>控件。 若要使用按钮列，必须手动创建它们，并将其添加到返回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>属性。  
  
 您可以通过处理响应用户单击按钮单元格在<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>事件。  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 使用<xref:System.Windows.Forms.DataGridViewComboBoxColumn>，可以显示包含下拉列表框的单元格的列。 这可用于仅包含特定值，例如 Northwind 示例数据库中的产品表的类别列的字段中输入数据。  
  
 您可以填充下拉列表用于在相同的方式将填充所有单元格<xref:System.Windows.Forms.ComboBox>下拉列表中，通过返回的集合手动<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>属性，或通过将其绑定到数据源通过<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>， <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>，和<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>属性。 有关详细信息，请参阅[组合框控件](combobox-control-windows-forms.md)。  
  
 您可以将实际的单元格的值绑定到使用的数据源<xref:System.Windows.Forms.DataGridView>通过设置控件<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>属性的<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>。  
  
 数据绑定时，不会自动生成组合框列<xref:System.Windows.Forms.DataGridView>控件。 若要使用组合框中的列，必须手动创建它们，并将其添加到返回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>属性。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 使用<xref:System.Windows.Forms.DataGridViewLinkColumn>，可以显示一列包含超链接的单元格。 这可用于数据源中或作为特殊行为，例如使用子记录打开一个窗口的按钮列的替代方法的 URL 值。  
  
 数据绑定时，不会自动生成链接列<xref:System.Windows.Forms.DataGridView>控件。 若要使用链接列，必须手动创建它们，并将其添加到返回的集合<xref:System.Windows.Forms.DataGridView.Columns%2A>属性。  
  
 您可以通过处理响应用户单击链接上<xref:System.Windows.Forms.DataGridView.CellContentClick>事件。 此事件是不同于<xref:System.Windows.Forms.DataGridView.CellClick>和<xref:System.Windows.Forms.DataGridView.CellMouseClick>事件，当用户单击任意位置的单元格中出现。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>类提供多个属性用于修改链接的外观之前,、 期间和之后在被单击。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView 控件](datagridview-control-windows-forms.md)
- [如何：在 Windows 窗体 DataGridView 控件的单元格中显示图像](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [如何：使用 Windows 窗体 DataGridView 控件中的图像列](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
