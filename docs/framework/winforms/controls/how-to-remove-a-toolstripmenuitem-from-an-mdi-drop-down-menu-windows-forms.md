---
title: 如何：从 MDI 下拉菜单 （Windows 窗体） 中删除 ToolStripMenuItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 6e0d453903b817e9acd743e835f4d466e3565271
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132829"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>如何：从 MDI 下拉菜单 （Windows 窗体） 中删除 ToolStripMenuItem
在某些应用程序中，多文档界面 (MDI) 子窗口的类型可以不同于 MDI 父窗口。 例如，MDI 父窗口可能为电子表格，而 MDI 子窗口可能为图表。 在这种情况下，由于激活了不同类型的 MDI 子窗口，你想用 MDI 子菜单上的内容更新 MDI 父菜单的内容。  
  
 以下过程使用<xref:System.Windows.Forms.Form.IsMdiContainer%2A>， <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>， <xref:System.Windows.Forms.MergeAction>，和<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>属性，以从 MDI 父菜单的下拉部分移除菜单项。 关闭 MDI 子窗口将移除的菜单项还原到 MDI 父菜单。  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>若要从 MDI 下拉菜单移除 MenuStrip  
  
1.  创建一个窗体并将其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 属性设置为 `true`。  
  
2.  将 <xref:System.Windows.Forms.MenuStrip> 添加到 `Form1` 并将 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 属性设置为 `true`。  
  
3.  添加到顶级菜单项`Form1`<xref:System.Windows.Forms.MenuStrip>并设置其<xref:System.Windows.Forms.Control.Text%2A>属性设置为`&File`。  
  
4.  添加到的三个子菜单项`&File`菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&Open`， `&Import from`，和`E&xit`。  
  
5.  添加到的两个子菜单项`&Import from`子菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&Word`和`&Excel`。  
  
6.  向项目添加窗体中，添加<xref:System.Windows.Forms.MenuStrip>到的窗体，并设置<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>的属性`Form2`<xref:System.Windows.Forms.MenuStrip>到`true`。  
  
7.  添加到顶级菜单项`Form2`<xref:System.Windows.Forms.MenuStrip>并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&File`。  
  
8.  添加`&Import from`子菜单项`&File`菜单`Form2`，并添加`&Word`子菜单项到`&File`菜单。  
  
9. 设置<xref:System.Windows.Forms.MergeAction>并<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>的属性`Form2`下表中所示的菜单项。  
  
    |Form2 的菜单项|MergeAction 值|MergeIndex 值|  
    |---------------------|-----------------------|----------------------|  
    |文件|MatchOnly|-1|  
    |从导入|MatchOnly|-1|  
    |字|删除|-1|  
  
10. 在中`Form1`，创建的事件处理程序<xref:System.Windows.Forms.Control.Click>事件的`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
11. 事件处理程序中插入类似于下面的代码示例，若要创建和显示的新实例的代码`Form2`作为的 MDI 子级`Form1`:  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. 将代码置于类似于下面的代码示例中`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>注册事件处理程序。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `Form1` 和 `Form2` 的两个 <xref:System.Windows.Forms.Form> 控件。  
  
-   `Form1` 上名为 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控件和 `Form2` 上名为 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- [如何：创建 MDI 父窗体](../advanced/how-to-create-mdi-parent-forms.md)
- [如何：创建 MDI 子窗体](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控件概述](menustrip-control-overview-windows-forms.md)
