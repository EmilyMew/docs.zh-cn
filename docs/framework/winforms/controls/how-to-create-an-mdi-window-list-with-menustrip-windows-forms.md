---
title: 如何：使用 （Windows 窗体） MenuStrip 创建 MDI 窗口列表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: bfe84ccb30b13b8232172749454bf8f3625269ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139199"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>如何：使用 （Windows 窗体） MenuStrip 创建 MDI 窗口列表
使用多文档界面 (MDI) 创建的应用程序可以打开多个文档在同一时间和复制并粘贴到另一个文档内容。  
  
 此过程演示如何创建父级的窗口菜单上的所有活动子窗体的列表。  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>若要在 MenuStrip 创建 MDI 窗口列表  
  
1.  创建一个窗体并将其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 属性设置为 `true`。  
  
2.  在窗体上添加一个 <xref:System.Windows.Forms.MenuStrip> 控件。  
  
3.  添加到两个顶级菜单项<xref:System.Windows.Forms.MenuStrip>并设置其<xref:System.Windows.Forms.Control.Text%2A>属性设置为`&File`和`&Window`。  
  
4.  将子菜单项添加到 `&File` 菜单项，并将其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 属性设置为 `&Open`。  
  
5.  设置<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>的属性<xref:System.Windows.Forms.MenuStrip>到`&Window`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
6.  向项目添加窗体并将所需的控件添加到它，例如另一个<xref:System.Windows.Forms.MenuStrip>。  
  
7.  创建事件处理程序<xref:System.Windows.Forms.Control.Click>事件的`&New`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
8.  事件处理程序中插入类似于以下内容，以创建和显示的新实例的代码`Form2`作为的 MDI 子级`Form1`。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. 将放置在以下代码`&New`<xref:System.Windows.Forms.ToolStripMenuItem>注册事件处理程序。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `Form1` 和 `Form2` 的两个 <xref:System.Windows.Forms.Form> 控件。  
  
-   `Form1` 上名为 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控件和 `Form2` 上名为 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- [如何：创建 MDI 父窗体](../advanced/how-to-create-mdi-parent-forms.md)
- [如何：创建 MDI 子窗体](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控件](menustrip-control-windows-forms.md)
