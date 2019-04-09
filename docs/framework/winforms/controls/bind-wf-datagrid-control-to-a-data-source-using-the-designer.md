---
title: 如何：使用设计器将 Windows 窗体 DataGrid 控件绑定到数据源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: a7b03ab5417eacf7962f2a05b674ceb45c7d558c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115721"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>如何：使用设计器将 Windows 窗体 DataGrid 控件绑定到数据源

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows 窗体<xref:System.Windows.Forms.DataGrid>控件专门设计用于显示数据源中的信息。 将控件在设计时绑定通过设置<xref:System.Windows.Forms.DataGrid.DataSource%2A>并<xref:System.Windows.Forms.DataGrid.DataMember%2A>属性，或在运行时通过调用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。 尽管可以显示来自各种数据源的数据，最典型的源是数据集和数据视图。  
  
 如果在设计时数据源，例如，如果该窗体包含一个数据集或数据视图的实例，则可以在设计时将网格绑定到数据源。 您可以预览数据网格中的显示效果。  
  
 此外可以在运行时以编程方式，绑定网格。 当你想要设置基于在运行时获取的信息的数据源时，这很有用。 例如，应用程序可能会让用户指定要查看的表的名称。 还有必要在数据源位置不存在在设计时的情况下。 这包括如数组、 集合、 非类型化数据集和数据读取器的数据源。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.DataGrid>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。 在 Visual Studio 2005 中，<xref:System.Windows.Forms.DataGrid>控件不在**工具箱**默认情况下。 考虑将其添加信息，请参阅[如何：将项添加到工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。 此外在 Visual Studio 2005 中，你可以使用**数据源**设计时数据绑定的窗口。 有关详细信息请参阅[将控件绑定到 Visual Studio 中的数据](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>若要对单个表设计器中数据绑定的 DataGrid 控件  
  
1.  设置控件的<xref:System.Windows.Forms.DataGrid.DataSource%2A>属性设置为包含你想要将绑定到的数据项目的对象。  
  
2.  如果数据集数据源，则设置<xref:System.Windows.Forms.DataGrid.DataMember%2A>属性设置为要绑定到的表的名称。  
  
3.  如果数据源的数据集或数据视图基于数据集表，将代码添加到窗体来填充数据集。  
  
     所使用的确切代码取决于数据集从何处获取数据。 如果要直接从数据库填充数据集，则通常会调用`Fill`的数据适配器，如下面的代码示例使用一个称为数据集来填充中所示方法`DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  （可选）将适当的表样式和列样式添加到网格中。  
  
     如果没有表样式，您将看到表中，但其格式设置很少，且所有列均可见。  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>若要对多个表中的数据集设计器中数据绑定的 DataGrid 控件  
  
1.  设置控件的<xref:System.Windows.Forms.DataGrid.DataSource%2A>属性设置为包含你想要将绑定到的数据项目的对象。  
  
2.  如果数据集包含相关的表 （即，如果它包含关系对象），请将<xref:System.Windows.Forms.DataGrid.DataMember%2A>属性设置为父表的名称。  
  
3.  编写代码以填充数据集。  
  
## <a name="see-also"></a>请参阅

- [DataGrid 控件概述](datagrid-control-overview-windows-forms.md)
- [如何：向 Windows 窗体 DataGrid 控件添加表和列](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid 控件](datagrid-control-windows-forms.md)
- [Windows 窗体数据绑定](../windows-forms-data-binding.md)
- [在 Visual Studio 中访问数据](/visualstudio/data-tools/accessing-data-in-visual-studio)
