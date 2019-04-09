---
title: 如何：使用设计器对 Windows 窗体 ListView 控件中的项进行分组
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 223c2a639fdb7a05506eca333a44ca31c0dae75f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136651"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>如何：使用设计器对 Windows 窗体 ListView 控件中的项进行分组
分组功能<xref:System.Windows.Forms.ListView>控件使您能够以分组方式显示项的相关的集。 由包含组标题的水平组标头在屏幕上分隔这些组。 可以使用<xref:System.Windows.Forms.ListView>组以使大型列表对项目分组按字母顺序，按日期，或任何其他逻辑分组的导航。 下图显示了一些分组的项。  
  
 ![ListView 组](./media/listviewgroups.gif "ListViewGroups")  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.ListView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
 若要启用分组，您必须首先创建一个或多个<xref:System.Windows.Forms.ListViewGroup>对象在设计器中或以编程方式。 一旦已定义的组，可以将项分配给它。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> 组是仅适用于[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]当应用程序调用<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。 在早期操作系统上与组相关的任何代码不起作用和组将不会出现。 有关详细信息，请参阅 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。  
>   
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>若要添加或删除在设计器中的组  
  
1.  在中**属性**窗口中，单击**省略号**(![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 按钮旁边<xref:System.Windows.Forms.ListView.Groups%2A>属性。  
  
     **ListViewGroup 集合编辑器**出现。  
  
2.  若要添加组，请单击**添加**按钮。 然后可以设置属性的新组，如<xref:System.Windows.Forms.ListViewGroup.Header%2A>和<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>属性。 若要删除某个组，选择它，然后单击**删除**按钮。  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>若要将项分配给在设计器中的组  
  
1.  在中**属性**窗口中，单击**省略号**(![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 按钮旁边<xref:System.Windows.Forms.ListView.Items%2A>属性。  
  
     **列表视图项集合编辑器**出现。  
  
2.  若要添加新项，请单击**添加**按钮。 然后可以设置属性的新项，如<xref:System.Windows.Forms.ListViewItem.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>属性。  
  
3.  选择<xref:System.Windows.Forms.ListViewItem.Group%2A>属性并从下拉列表中选择一个组。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView 控件](listview-control-windows-forms.md)
- [ListView 控件概述](listview-control-overview-windows-forms.md)
- [如何：使用 Windows 窗体 ListView 控件添加和移除项](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
