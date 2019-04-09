---
title: 如何：确定已单击的 TreeView 节点 （Windows 窗体）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 073b953d2a39b27081020c56399ea3beae2083e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189568"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>如何：确定已单击的 TreeView 节点 （Windows 窗体）
使用 Windows 窗体时<xref:System.Windows.Forms.TreeView>控件，一项常见任务是确定哪个节点被单击，并相应做出响应。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>若要确定被单击的 TreeView 节点  
  
1.  使用<xref:System.EventArgs>对象返回到的被单击的节点对象的引用。  
  
2.  确定通过检查被单击的节点<xref:System.Windows.Forms.TreeViewEventArgs>类，该类包含与事件相关的数据。  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  作为替代方法，你可以使用<xref:System.Windows.Forms.MouseEventArgs>的<xref:System.Windows.Forms.Control.MouseDown>或<xref:System.Windows.Forms.Control.MouseUp>要获取事件<xref:System.Drawing.Point.X%2A>并<xref:System.Drawing.Point.Y%2A>坐标的值<xref:System.Drawing.Point>单击发生处。 然后，使用<xref:System.Windows.Forms.TreeView>控件的<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>方法，以确定被单击的节点。  
  
## <a name="see-also"></a>请参阅

- [TreeView 控件](treeview-control-windows-forms.md)
