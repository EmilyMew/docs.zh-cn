---
title: 如何：使用设计器将 Windows 窗体 DataGridView 控件中的列设为只读
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 8639c1e6f4382c1f91ed2c777b1b0ff29c5a60a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113511"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用设计器将 Windows 窗体 DataGridView 控件中的列设为只读
默认情况下，用户可以修改文本和在 Windows 窗体中显示的数字数据<xref:System.Windows.Forms.DataGridView>控件。 如果你想要显示不希望修改的数据，必须进行包含只读数据的列。 有关如何使控件完全只读的信息，请参阅[如何：防止行中添加和删除 Windows 窗体 DataGridView 控件使用设计器](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.DataGridView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a>若要使用设计器使列成为只读  
  
1.  单击智能标记标志符号 (![智能标记标志符号](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控件，然后选择**编辑列**。  
  
2.  选择一列从**选定列**列表。  
  
3.  在中**列属性**网格中，设置<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A>属性设置为`true`。  
  
    > [!NOTE]
    >  您还可以列只读时通过选择添加**Read Only**中的复选框**添加列**对话框。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [如何：使用设计器添加和移除 Windows 窗体 DataGridView 控件中的列](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用设计器防止在 Windows 窗体 DataGridView 控件中添加和删除行](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：向 Windows 窗体添加控件](how-to-add-controls-to-windows-forms.md)
