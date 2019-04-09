---
title: 如何：在 Windows 窗体 DataGrid 控件中删除或隐藏列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: e6e8a4a5908d890d34ab6de952917cd97be2b433
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120141"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>如何：在 Windows 窗体 DataGrid 控件中删除或隐藏列
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 你可以以编程方式删除或隐藏在 Windows 窗体中的列<xref:System.Windows.Forms.DataGrid>控件中使用的属性和方法<xref:System.Windows.Forms.GridColumnStylesCollection>并<xref:System.Windows.Forms.DataGridColumnStyle>对象 (的成员<xref:System.Windows.Forms.DataGridTableStyle>类)。  
  
 网格绑定到和仍然可以以编程方式访问数据源中仍存在的已删除或隐藏列。 它们不再只是在数据网格中可见。  
  
> [!NOTE]
>  如果你的应用程序不会访问某些列的数据，并且不希望它们显示在数据网格中，然后它不可能需要将其第一个位置中包含数据源中。  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>若要以编程方式从数据网格中删除列  
  
1.  在你的窗体声明区域中，声明的新实例<xref:System.Windows.Forms.DataGridTableStyle>类。  
  
2.  设置<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType>属性设置为你想要应用该样式在数据源中的表。 下面的示例使用<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>属性，它假定已设置。  
  
3.  添加新<xref:System.Windows.Forms.DataGridTableStyle>到 datagrid 的表样式集合的对象。  
  
4.  调用<xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.DataGrid>的<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>集合，指定要删除的列的列索引。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>若要以编程方式隐藏数据网格中的列  
  
1.  在你的窗体声明区域中，声明的新实例<xref:System.Windows.Forms.DataGridTableStyle>类。  
  
2.  设置<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>属性的<xref:System.Windows.Forms.DataGridTableStyle>到您想要应用该样式的数据源中的表。 下面的代码示例使用<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>属性，它假定已设置。  
  
3.  添加新<xref:System.Windows.Forms.DataGridTableStyle>到 datagrid 的表样式集合的对象。  
  
4.  通过设置隐藏的列及其`Width`属性设为 0，指定要隐藏的列的列索引。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>请参阅

- [如何：更改 Windows 窗体 DataGrid 控件中在运行时显示的数据](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [如何：向 Windows 窗体 DataGrid 控件添加表和列](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
