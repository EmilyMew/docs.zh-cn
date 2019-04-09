---
title: 如何：设置状态栏面板的大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: c6c9d6570e9b5c2f6d4eee0262c3d90e29e4b493
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131048"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>如何：设置状态栏面板的大小
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> 控件取代了 <xref:System.Windows.Forms.StatusBar> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.StatusBar> 控件以实现向后兼容并供将来使用。  
  
 每个实例<xref:System.Windows.Forms.StatusBarPanel>类中[StatusBar 控件](statusbar-control-windows-forms.md)控件具有多个动态属性，以确定其宽度和在运行时重设大小行为。  
  
### <a name="to-set-the-size-of-a-panel"></a>若要设置面板的大小  
  
1.  在过程中，设置<xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>， <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>，并<xref:System.Windows.Forms.StatusBarPanel.Width%2A>属性 (或任何子集其中) 为状态栏面板使用它们的索引传递<xref:System.Windows.Forms.StatusBar.Panels%2A>属性<xref:System.Windows.Forms.StatusBarPanel>集合。  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [演练：在运行时更新状态栏信息](walkthrough-updating-status-bar-information-at-run-time.md)
- [如何：确定 Windows 窗体 StatusBar 控件中被单击的面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控件概述](statusbar-control-overview-windows-forms.md)
