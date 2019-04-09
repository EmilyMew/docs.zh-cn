---
title: 如何：使用设计器添加和移除 Windows 窗体 DataGridView 控件中的列
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 82bab7a42c7a8de131cc53d792cf2d372580af40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078104"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用设计器添加和移除 Windows 窗体 DataGridView 控件中的列
Windows 窗体<xref:System.Windows.Forms.DataGridView>控件必须包含的列才能显示数据。 如果您计划手动填充该控件，您必须自行添加的列。 或者，可以将控件绑定到数据源，生成并自动填充列。 如果数据源包含多于你想要显示的列数，则可以删除不需要的列。  
  
 下面的过程要求**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.DataGridView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-a-column-using-the-designer"></a>若要添加使用设计器的列  
  
1.  单击智能标记标志符号 (![智能标记标志符号](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控件，然后选择**添加列**。  
  
2.  在中**添加列**对话框框中，选择**数据绑定列**选项和从数据源中，选择一列或选择**未绑定列**选项，并将列定义使用提供的字段。  
  
3.  单击**添加**按钮添加的列，使其出现在设计器中，如果现有的列已填入控件显示区域。  
  
    > [!NOTE]
    >  您可以修改列属性中的**编辑列**对话框中，使用户能够从控件的智能标记。  
  
### <a name="to-remove-a-column-using-the-designer"></a>若要删除某一列使用设计器  
  
1.  选择**编辑列**从控件的智能标记。  
  
2.  选择一列从**选定列**列表。  
  
3.  单击**删除**按钮以删除列，使其从设计器中消失。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- [如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：向 Windows 窗体添加控件](how-to-add-controls-to-windows-forms.md)
