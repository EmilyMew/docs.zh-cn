---
title: 何时使用 Windows 窗体 ComboBox 而非 ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 8a2429049acf1a22edde8d132ece17da4e91f1db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111418"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>何时使用 Windows 窗体 ComboBox 而非 ListBox
<xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ListBox>控件具有类似的行为，并在某些情况下可能是可互换。 有些的时候，但是，当一个或另一个是更适合于任务。  
  
 通常情况下，组合框进行了适当，有一组建议的选择，而列表框适合于你想要将输入限制为位于列表上。 组合框包含一个文本字段，因此可以在键入不在列表的选项。 例外情况是何时<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>属性设置为<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>。 在这种情况下，该控件将选择一个项，如果键入其第一个字母。  
  
 此外，组合框在窗体上节省空间。 因为，只有在用户单击向下箭头，不显示的完整列表，组合框可以方便地放入列表框中放不下的小空间。 例外情况是何时<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>属性设置为<xref:System.Windows.Forms.ComboBoxStyle.Simple>： 显示的完整列表，并且占用更多的空间不是列表框将组合框。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [如何：在 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件中添加或移除项](add-and-remove-items-from-a-wf-combobox.md)
- [如何：对 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件的内容排序](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [用于列出选项的 Windows 窗体控件](windows-forms-controls-used-to-list-options.md)
