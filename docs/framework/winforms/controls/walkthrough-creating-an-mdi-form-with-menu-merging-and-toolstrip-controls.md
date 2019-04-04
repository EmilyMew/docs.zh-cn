---
title: 演练：创建具有菜单合并功能和 ToolStrip 控件的 MDI 窗体
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 49d9b10d8a87af1c3600756efe8dba3f81df90a6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717130"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>演练：创建具有菜单合并功能和 ToolStrip 控件的 MDI 窗体
<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间支持多文档界面 (MDI) 应用程序，而 <xref:System.Windows.Forms.MenuStrip> 控件支持菜单合并。 MDI 窗体还可支持 <xref:System.Windows.Forms.ToolStrip> 控件。  
  
 本演练演示如何使用<xref:System.Windows.Forms.ToolStripPanel>具有的 MDI 窗体的控件。 此窗体还支持菜单与子菜单合并。 在本演练阐释了以下任务：  
  
-   创建一个 Windows 窗体项目。  
  
-   正在创建你的窗体的主菜单。 在菜单的实际名称将有所不同。  
  
-   添加<xref:System.Windows.Forms.ToolStripPanel>控制对**工具箱**。  
  
-   创建子窗体。  
  
-   排列<xref:System.Windows.Forms.ToolStripPanel>按 z 顺序的控件。  
  
 完成，你将拥有支持菜单合并功能和可移动的 MDI 窗体<xref:System.Windows.Forms.ToolStrip>控件。  
  
 要将本主题中的代码作为单个列表进行复制，请参阅[如何：创建具有菜单合并功能和 ToolStrip 控件的 MDI 窗体](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，你将需要：  
  
-   若要能够创建和安装 Visual Studio 的计算机上运行 Windows 窗体应用程序项目的足够权限。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建项目并设置窗体。  
  
#### <a name="to-create-the-project"></a>要创建项目  
  
1.  创建一个名为 Windows 应用程序项目**mdi 窗体**(**文件** > **新建** > **项目** > **Visual C#** 或**Visual Basic** > **经典桌面** > **Windows 窗体应用程序**).  
  
2.  在 Windows 窗体设计器中，选择窗体。  
  
3.  在属性窗口中设置的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>到`true`。  
  
## <a name="creating-the-main-menu"></a>创建主菜单  
 MDI 父窗体包含主菜单。 主菜单有一个名为菜单项**窗口**。 与**窗口**菜单项，可以创建子窗体。 从子窗体的菜单项合并到主菜单中。  
  
#### <a name="to-create-the-main-menu"></a>若要创建主菜单  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.MenuStrip>拖到窗体控件。  
  
2.  添加<xref:System.Windows.Forms.ToolStripMenuItem>到<xref:System.Windows.Forms.MenuStrip>控制并将其命名**窗口**。  
  
3.  选择 <xref:System.Windows.Forms.MenuStrip> 控件。  
  
4.  在属性窗口中设置的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>属性设置为`ToolStripMenuItem1`。  
  
5.  添加到子项**窗口**菜单项，并将其命名**新建**。  
  
6.  在属性窗口中，单击**事件**。  
  
7.  双击<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
     Windows 窗体设计器生成的事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
8.  以下代码插入到的事件处理程序。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>向工具箱添加 ToolStripPanel 控件  
 当你使用<xref:System.Windows.Forms.MenuStrip>必须具有的 MDI 窗体控件<xref:System.Windows.Forms.ToolStripPanel>控件。 必须添加<xref:System.Windows.Forms.ToolStripPanel>控制对**工具箱**来生成你在 Windows 窗体设计器中的 MDI 窗体。  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel 控件添加到工具箱  
  
1.  打开**工具箱**，然后单击**所有 Windows 窗体**选项卡以显示可用的 Windows 窗体控件。  
  
2.  若要打开快捷菜单中，右键单击并选择**选择项**。  
  
3.  在中**选择工具箱项**对话框中，向下滚动**名称**列，直到找到**ToolStripPanel**。  
  
4.  选中的复选框**ToolStripPanel**，然后单击**确定**。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控件会出现在**工具箱**。  
  
## <a name="creating-a-child-form"></a>创建子窗体  
 在此过程中，您将定义具有其自己的单独的子窗体类<xref:System.Windows.Forms.MenuStrip>控件。 此窗体的菜单项将与父窗体的合并。  
  
#### <a name="to-define-a-child-form"></a>若要定义子窗体  
  
1.  添加名为一个新窗体`ChildForm`到项目。  
  
     有关详细信息，请参阅[如何：向项目添加 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))。  
  
2.  从**工具箱**，拖动<xref:System.Windows.Forms.MenuStrip>到子窗体上的控件。  
  
3.  单击<xref:System.Windows.Forms.MenuStrip>控件的智能标记标志符号 (![智能标记标志符号](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然后选择**编辑项**。  
  
4.  在中**项集合编辑器**对话框框中，添加一个新<xref:System.Windows.Forms.ToolStripMenuItem>名为**ChildMenuItem**到子菜单。  
  
     有关详细信息，请参阅[ToolStrip 项集合编辑器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))。  
  
## <a name="testing-the-form"></a>测试窗体  
  
#### <a name="to-test-your-form"></a>若要测试你的窗体  
  
1.  按 F5 编译并运行你的窗体。  
  
2.  单击**窗口**菜单项以打开菜单，然后单击**新建**。  
  
     窗体的 MDI 客户端区域中创建新的子窗体。 与主菜单合并子窗体的菜单。  
  
3.  关闭子窗体。  
  
     从主菜单中删除子窗体的菜单。  
  
4.  单击**新建**几次。  
  
     子窗体自动列入**窗口**菜单项，因为<xref:System.Windows.Forms.MenuStrip>控件的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>分配属性。  
  
## <a name="adding-toolstrip-support"></a>添加 ToolStrip 的支持  
 在此过程中，您将添加四个<xref:System.Windows.Forms.ToolStrip>到 MDI 父窗体控件。 每个<xref:System.Windows.Forms.ToolStrip>控件添加内部<xref:System.Windows.Forms.ToolStripPanel>控件停靠到窗体的边缘。  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>若要添加到 MDI 父窗体的 ToolStrip 控件  
  
1.  从**工具箱**，拖动<xref:System.Windows.Forms.ToolStripPanel>拖到窗体控件。  
  
2.  与<xref:System.Windows.Forms.ToolStripPanel>控件处于选中状态，双击<xref:System.Windows.Forms.ToolStrip>控制**工具箱**。  
  
     一个<xref:System.Windows.Forms.ToolStrip>控件中创建<xref:System.Windows.Forms.ToolStripPanel>控件。  
  
3.  选择 <xref:System.Windows.Forms.ToolStripPanel> 控件。  
  
4.  在属性窗口更改控件的值<xref:System.Windows.Forms.Control.Dock%2A>属性设置为<xref:System.Windows.Forms.DockStyle.Left>。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控件停靠到窗体中，主菜单下的左侧。 在 MDI 工作区调整大小以适合<xref:System.Windows.Forms.ToolStripPanel>控件。  
  
5.  重复步骤 1 至 4。  
  
     停靠新<xref:System.Windows.Forms.ToolStripPanel>到窗体顶部的控件。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控件下方主菜单中，但第一个右侧停靠<xref:System.Windows.Forms.ToolStripPanel>控件。 本步骤说明了在正确定位的 z 顺序的重要性<xref:System.Windows.Forms.ToolStripPanel>控件。  
  
6.  对两个重复步骤 1 到 4<xref:System.Windows.Forms.ToolStripPanel>控件。  
  
     停靠新<xref:System.Windows.Forms.ToolStripPanel>向右侧和底部的窗体控件。  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>排列按 Z 顺序的 ToolStripPanel 控件  
 停靠的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 窗体上的控件由 z 顺序中的控件的位置。 您可以轻松地排列在文档大纲窗口中控件的 z 顺序。  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>若要排列按 Z 顺序的 ToolStripPanel 控件  
  
1.  在中**视图**菜单上，单击**其他 Windows**，然后单击**文档大纲**。  
  
     排列方式在<xref:System.Windows.Forms.ToolStripPanel>控件从前面的过程是使用了非标准。 这是因为 z 顺序不正确。 使用文档大纲窗口更改控件的 z 顺序。  
  
2.  在文档大纲窗口中，选择**ToolStripPanel4**。  
  
3.  单击向下箭头按钮重复，直到**ToolStripPanel4**位于列表的底部。  
  
     **ToolStripPanel4**控件停靠到窗体中，在其他控件下的底部。  
  
4.  选择**ToolStripPanel2**。  
  
5.  一次单击向下箭头按钮以在列表中第三个放置控件。  
  
     **ToolStripPanel2**控件停靠到窗体，下面的主菜单和高于其他控件的顶部。  
  
6.  选择中的各个控件**文档大纲**窗口并将它们移动到不同的 z 顺序中的位置。 请注意对停靠控件的位置的 z 顺序的影响。 使用 CTRL-Z 或**撤消**上**编辑**菜单上，若要撤消所做的更改。  
  
## <a name="checkpoint"></a>检查点  
  
#### <a name="to-test-your-form"></a>若要测试你的窗体  
  
1.  按 F5 编译并运行你的窗体。  
  
2.  单击的手柄<xref:System.Windows.Forms.ToolStrip>控件，窗体上将控件拖到不同的位置。  
  
     可以拖动<xref:System.Windows.Forms.ToolStrip>控件从一个<xref:System.Windows.Forms.ToolStripPanel>到另一个控件。  
  
## <a name="next-steps"></a>后续步骤  
 在本演练中，您创建了一个 MDI 父窗体<xref:System.Windows.Forms.ToolStrip>控件和菜单合并。 可以使用<xref:System.Windows.Forms.ToolStrip>实现多种其他用途的控件的系列：  
  
-   创建与控件的快捷菜单<xref:System.Windows.Forms.ContextMenuStrip>。 有关详细信息，请参阅[ContextMenu 组件概述](contextmenu-component-overview-windows-forms.md)。  
  
-   创建一个自动填充的标准菜单的窗体。 有关详细信息，请参见[演练：向窗体提供标准菜单项](walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   提供你<xref:System.Windows.Forms.ToolStrip>控件专业的外观。 有关详细信息，请参阅[如何：设置 ToolStrip 呈现程序](how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [如何：创建 MDI 父窗体](../advanced/how-to-create-mdi-parent-forms.md)
- [如何：创建 MDI 子窗体](../advanced/how-to-create-mdi-child-forms.md)
- [如何：将 MenuStrip 插入 MDI 下拉菜单](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [ToolStrip 控件](toolstrip-control-windows-forms.md)
