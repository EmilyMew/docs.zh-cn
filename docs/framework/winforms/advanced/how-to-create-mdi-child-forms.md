---
title: 如何：创建 MDI 子窗体
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 83f94830eec1d82112719a48e8ea98e2503f4542
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124522"
---
# <a name="how-to-create-mdi-child-forms"></a>如何：创建 MDI 子窗体
MDI 子窗体是不可或缺的要素[多文档界面 (MDI) 应用程序](multiple-document-interface-mdi-applications.md)，因为这些窗体是用户交互的中心。  
  
 在下面的过程中，将创建显示 <xref:System.Windows.Forms.RichTextBox> 控件的 MDI 子窗体，该子窗体类似于大多数字处理应用程序。 将 <xref:System.Windows.Forms> 控件替换为其他控件（如 <xref:System.Windows.Forms.DataGridView> 控件或混合控件）使你能够创建各种可能的 MDI 子窗口（并且进一步扩展为 MDI 应用程序）。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-mdi-child-forms"></a>创建 MDI 子窗体  
  
1.  创建新的 Windows 窗体项目。 在中**属性 Windows**对于窗体中，设置其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>属性设置为`true`，并将其`WindowsState`属性设置为`Maximized`。  
  
     这将该表单指定为适合子窗口的 MDI 容器。  
  
2.  将 <xref:System.Windows.Forms.MenuStrip> 控件从 `Toolbox` 中拖到窗体上。 设置其`Text`属性设置为**文件**。  
  
3.  单击省略号 （...） 下一步**项**属性，并单击**添加**添加两个子工具条菜单项。 设置`Text`到这些项的属性**新建**并**窗口**。  
  
4.  在中**解决方案资源管理器**，右键单击项目，依次指向**添加**，然后选择**添加新项**。  
  
5.  在中**添加新项**对话框中，选择**Windows 窗体**（在 Visual Basic 或 Visual C# 中） 或**Windows 窗体应用程序 (.NET)** (在[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 从**模板**窗格。 在中**名称**框中，将窗体**Form2**。 单击**打开**按钮将窗体添加到项目。  
  
    > [!NOTE]
    >  在此步骤中创建的 MDI 子窗体是标准的 Windows 窗体。 因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 属性，该属性允许你控制窗体的透明度。 但是，<xref:System.Windows.Forms.Form.Opacity%2A> 属性旨在用于顶级窗口。 不要将其与 MDI 子窗体同时使用，否则可能会引起绘制问题。  
  
     此窗体将作为 MDI 子窗体的模板。  
  
     **Windows 窗体设计器**打开，其中显示**Form2**。  
  
6.  从**工具箱**，拖动**RichTextBox**到窗体控件。  
  
7.  在中**属性**窗口中，将`Anchor`属性设置为**左上**并`Dock`属性设置为**填充**。  
  
     这导致即使在调整 MDI 子窗体的大小，<xref:System.Windows.Forms.RichTextBox> 控件也会完全填充该窗体的区域。  
  
8.  双击**新建**菜单项创建<xref:System.Windows.Forms.Control.Click>事件处理程序。  
  
9. 插入代码类似于以下内容，以创建新的 MDI 子窗体，当用户单击**新建**菜单项。  
  
    > [!NOTE]
    >  在下面的示例中，事件处理程序处理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。 请注意，具体取决于您应用程序的体系结构，你**新建**菜单项可能不是`MenuItem2`。  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中，在 Form1.h 顶部添加下面的 `#include` 指令：  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. 在顶部的下拉列表中**属性**窗口中，选择对应于在菜单栏**文件**菜单条，然后设置<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>属性设置为窗口<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
     这样，便**窗口**菜单能够维护打开的 MDI 子窗口在活动子窗口的旁边的复选标记的列表。  
  
11. 按 F5 运行该应用程序。 通过选择**新建**从**文件**菜单中，可以创建新 MDI 子窗体，这是保留在跟踪的**窗口**菜单项。  
  
    > [!NOTE]
    >  当 MDI 子窗体具有一个 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构），而且它在有 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构）的 MDI 父窗体中打开时，如果设置了 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性（或 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性），这些菜单项就会自动合并。 将两个 <xref:System.Windows.Forms.MainMenu> 组件的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性和子窗体的所有菜单项设置为 <xref:System.Windows.Forms.MenuMerge.MergeItems>。 此外，设置 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性，以便这两个菜单的菜单项按所需顺序显示。 此外，请记住，关闭 MDI 父窗体时，每个 MDI 子窗体先引发一个 <xref:System.Windows.Forms.Form.Closing> 事件，再引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件。 取消 MDI 子窗体的 <xref:System.Windows.Forms.Form.Closing> 事件将不会阻止引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件；但是，MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 参数将设置为 `true`。 通过将 <xref:System.ComponentModel.CancelEventArgs> 参数设置为 `false` 可以强制 MDI 父窗体和所有 MDI 子窗体关闭。  
  
## <a name="see-also"></a>请参阅

- [多文档界面 (MDI) 应用程序](multiple-document-interface-mdi-applications.md)
- [如何：创建 MDI 父窗体](how-to-create-mdi-parent-forms.md)
- [如何：确定活动的 MDI 子窗体](how-to-determine-the-active-mdi-child.md)
- [如何：将数据发送到活动的 MDI 子窗体](how-to-send-data-to-the-active-mdi-child.md)
- [如何：排列 MDI 子窗体](how-to-arrange-mdi-child-forms.md)
