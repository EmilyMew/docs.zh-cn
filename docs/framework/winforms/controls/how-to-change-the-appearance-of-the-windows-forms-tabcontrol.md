---
title: 如何：更改 Windows 窗体 TabControl 的外观
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: c84ce67225b70933e65b8f88da1eaef6b1f3de99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133128"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>如何：更改 Windows 窗体 TabControl 的外观
可以使用的属性来更改 Windows 窗体中的选项卡的外观<xref:System.Windows.Forms.TabControl>和<xref:System.Windows.Forms.TabPage>构成控件上的各个选项卡对象。 通过设置这些属性，可以在选项卡上显示的图像、 显示垂直而不是水平选项卡、 显示多个行的选项卡上，并启用或以编程方式禁用选项卡。  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>若要显示一个图标上的一个选项卡的标签部分  
  
1.  添加<xref:System.Windows.Forms.ImageList>到窗体控件。  
  
2.  将映像添加到图像列表。  
  
     有关图像列表的详细信息，请参阅[ImageList 组件](imagelist-component-windows-forms.md)和[如何：添加或删除图像与 Windows 窗体 ImageList 组件](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
3.  设置<xref:System.Windows.Forms.TabControl.ImageList%2A>的属性<xref:System.Windows.Forms.TabControl>到<xref:System.Windows.Forms.ImageList>控件。  
  
4.  设置<xref:System.Windows.Forms.TabPage.ImageIndex%2A>属性的<xref:System.Windows.Forms.TabPage>到列表中的相应图像的索引。  
  
### <a name="to-create-multiple-rows-of-tabs"></a>若要创建多个行的选项卡  
  
1.  添加所需的选项卡页的数目。  
  
2.  设置<xref:System.Windows.Forms.TabControl.Multiline%2A>的属性<xref:System.Windows.Forms.TabControl>到`true`。  
  
3.  如果选项卡尚未显示在多行中，设置<xref:System.Windows.Forms.Control.Width%2A>属性的<xref:System.Windows.Forms.TabControl>为窄于所有选项卡。  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>若要排列控件的一侧的选项卡  
  
-   设置<xref:System.Windows.Forms.TabControl.Alignment%2A>的属性<xref:System.Windows.Forms.TabControl>到<xref:System.Windows.Forms.TabAlignment.Left>或<xref:System.Windows.Forms.TabAlignment.Right>。  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>若要以编程方式启用或禁用选项卡上的所有控件  
  
1.  设置<xref:System.Windows.Forms.TabPage.Enabled%2A>的属性<xref:System.Windows.Forms.TabPage>到`true`或`false`。  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>若要为按钮显示的选项卡  
  
-   设置<xref:System.Windows.Forms.TabControl.Appearance%2A>的属性<xref:System.Windows.Forms.TabControl>到<xref:System.Windows.Forms.TabAppearance.Buttons>或<xref:System.Windows.Forms.TabAppearance.FlatButtons>。  
  
## <a name="see-also"></a>请参阅

- [TabControl 控件](tabcontrol-control-windows-forms.md)
- [TabControl 控件概述](tabcontrol-control-overview-windows-forms.md)
- [如何：将控件添加到选项卡页](how-to-add-a-control-to-a-tab-page.md)
- [如何：禁用选项卡页](how-to-disable-tab-pages.md)
- [如何：使用 Windows 窗体 TabControl 添加和移除选项卡](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
