---
title: ListBox 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
ms.openlocfilehash: f70246d4a4d158815ee9662036eca8edeb891d85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104191"
---
# <a name="listbox-control-overview-windows-forms"></a>ListBox 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.ListBox>控件显示用户可以从中选择一个或多个项列表。 如果总项数超出可显示的数字，滚动条自动添加到<xref:System.Windows.Forms.ListBox>控件。 当<xref:System.Windows.Forms.ListBox.MultiColumn%2A>属性设置为`true`、 列表框中显示多个列中的项和水平滚动条的显示。 当<xref:System.Windows.Forms.ListBox.MultiColumn%2A>属性设置为`false`、 列表框中显示的单个列中的项和垂直滚动条的显示。 当<xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A>设置为`true`，该滚动条显示而不考虑项的数目。 <xref:System.Windows.Forms.ListBox.SelectionMode%2A>属性确定一次可以选择多少个列表项。  
  
## <a name="ways-to-change-the-listbox-control"></a>若要更改 ListBox 控件的方式  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>属性返回对应的整数值的列表框中的第一个所选项目。 你可以以编程方式更改选定的项，通过更改<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>代码中的值; 将 Windows 窗体上突出显示列表中的相应项。 如果未不选择任何项，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值为-1。 如果选择列表中的第一项，则<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值为 0。 当选择了多个项时，<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值反映在列表中最先出现的选定的项。 <xref:System.Windows.Forms.ListBox.SelectedItem%2A>属性是类似于<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>，但返回项本身，而通常一个字符串值。 <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>属性反映了在列表中，项的数目和的值<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A>属性始终为一个超过最大可能<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>值，因为<xref:System.Windows.Forms.ListBox.SelectedIndex%2A>是从零开始。  
  
 若要添加或删除中的项<xref:System.Windows.Forms.ListBox>控制，请使用<xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>， <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>，<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A>或<xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>方法。 或者，您可以向列表添加项使用<xref:System.Windows.Forms.ListBox.Items%2A>在设计时属性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ListBox>
- [如何：在 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件中添加或移除项](add-and-remove-items-from-a-wf-combobox.md)
- [如何：对 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件的内容排序](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [如何：将 Windows 窗体 ComboBox 控件或 ListBox 控件绑定到数据](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [ComboBox 控件概述](combobox-control-overview-windows-forms.md)
- [CheckedListBox 控件概述](checkedlistbox-control-overview-windows-forms.md)
- [用于列出选项的 Windows 窗体控件](windows-forms-controls-used-to-list-options.md)
- [如何：为 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件创建查找表](create-a-lookup-table-for-a-wf-combobox-listbox.md)
