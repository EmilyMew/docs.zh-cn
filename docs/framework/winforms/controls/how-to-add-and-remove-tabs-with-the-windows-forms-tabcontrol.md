---
title: 如何：使用 Windows 窗体 TabControl 添加和移除选项卡
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 723e05803b1f7d2bc56476248987085dbe5e23f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101596"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>如何：使用 Windows 窗体 TabControl 添加和移除选项卡
默认情况下<xref:System.Windows.Forms.TabControl>控件包含两个<xref:System.Windows.Forms.TabPage>控件。 您可以访问通过这些选项卡<xref:System.Windows.Forms.TabControl.TabPages%2A>属性。  
  
### <a name="to-add-a-tab-programmatically"></a>若要以编程方式添加选项卡  
  
-   使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>属性。  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a>若要以编程方式删除选项卡  
  
-   若要删除所选的选项卡，请使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>属性。  
  
     或  
  
-   若要删除所有选项卡，请使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A>方法的<xref:System.Windows.Forms.TabControl.TabPages%2A>属性。  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a>请参阅

- [TabControl 控件概述](tabcontrol-control-overview-windows-forms.md)
- [如何：将控件添加到选项卡页](how-to-add-a-control-to-a-tab-page.md)
- [如何：禁用选项卡页](how-to-disable-tab-pages.md)
- [如何：更改 Windows 窗体 TabControl 的外观](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
