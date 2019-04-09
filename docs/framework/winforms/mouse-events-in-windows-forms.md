---
title: Windows 窗体中的鼠标事件
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 62309bb9965d1aa538e211dc66c44876671e0242
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134974"
---
# <a name="mouse-events-in-windows-forms"></a>Windows 窗体中的鼠标事件
当处理鼠标输入时，通常想要知道鼠标指针的位置和鼠标按钮的状态。 本主题详细介绍如何从鼠标事件获取此信息，并说明在 Windows 窗体控件中引发的鼠标单击事件的顺序。 列表和所有鼠标事件的说明，请参阅[鼠标输入工作原理在 Windows 窗体中](how-mouse-input-works-in-windows-forms.md)。  另请参阅[事件处理程序概述 （Windows 窗体）](event-handlers-overview-windows-forms.md)并[事件概述 （Windows 窗体）](events-overview-windows-forms.md)。  
  
## <a name="mouse-information"></a>鼠标信息  
 <xref:System.Windows.Forms.MouseEventArgs> 将发送到与单击鼠标按钮和跟踪鼠标移动相关的鼠标事件处理程序。 <xref:System.Windows.Forms.MouseEventArgs> 提供有关鼠标，包括在工作区坐标，而按下鼠标按钮，是否已经滚动鼠标滚轮的鼠标指针位置的当前状态信息。 几个鼠标事件（例如通知鼠标指针进入或离开控件边界的时间）会向事件处理程序发送 <xref:System.EventArgs>，但不提供详细信息。  
  
 如果想要知道鼠标按钮当前的状态或鼠标指针的位置，并且希望避免处理鼠标事件，还可以使用 <xref:System.Windows.Forms.Control> 类的 <xref:System.Windows.Forms.Control.MouseButtons%2A> 和 <xref:System.Windows.Forms.Control.MousePosition%2A> 属性。 <xref:System.Windows.Forms.Control.MouseButtons%2A> 返回有关哪些鼠标按钮当前按下的信息。 <xref:System.Windows.Forms.Control.MousePosition%2A> 返回鼠标指针的屏幕坐标，等同于由 <xref:System.Windows.Forms.Cursor.Position%2A> 返回的值。  
  
## <a name="converting-between-screen-and-client-coordinates"></a>在屏幕坐标和客户端坐标之间转换  
 由于某些鼠标位置信息以客户端坐标提供，另一些以屏幕坐标提供，因此可能需要将某个点的位置信息从一个坐标系统转换到另一个坐标系统。 通过使用 <xref:System.Windows.Forms.Control> 类提供的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法可轻松完成此操作。  
  
## <a name="standard-click-event-behavior"></a>标准单击事件行为  
 如果想要以正确的顺序处理鼠标单击事件，则需要了解在 Windows 窗体控件中引发的单击事件的顺序。 当按下鼠标按钮（不论哪个鼠标按钮）并释放时，所有 Windows 窗体控件将以相同的顺序引发单击事件，下表中注明的个别控件除外： 下表显示单击鼠标按钮所引发事件的顺序：  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> 事件的参数。  
  
2.  <xref:System.Windows.Forms.Control.Click> 事件的参数。  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> 事件的参数。  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> 事件的参数。  
  
 下表显示双击鼠标按钮所引发事件的顺序：  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> 事件的参数。  
  
2.  <xref:System.Windows.Forms.Control.Click> 事件的参数。  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> 事件的参数。  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> 事件的参数。  
  
5.  <xref:System.Windows.Forms.Control.MouseDown> 事件的参数。  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick> 事件的参数。 （此顺序可能不同，具体取决于相关控件的 <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> 样式位是否设置为 `true`。 有关如何设置 <xref:System.Windows.Forms.ControlStyles> 位的详细信息，请参阅 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法。）  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick> 事件的参数。  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> 事件的参数。  
  
 有关代码示例演示顺序的鼠标单击事件，请参阅[如何：事件在 Windows 窗体控件中处理用户输入](how-to-handle-user-input-events-in-windows-forms-controls.md)。  
  
### <a name="individual-controls"></a>个别控件  
 以下控件不符合标准鼠标单击事件行为：  
  
-   <xref:System.Windows.Forms.Button><xref:System.Windows.Forms.CheckBox>， <xref:System.Windows.Forms.ComboBox>，和<xref:System.Windows.Forms.RadioButton>控件  
  
    > [!NOTE]
    >  对于 <xref:System.Windows.Forms.ComboBox> 控件，如果用户单击编辑字段、按钮或列表中的某个项，将发生稍后详细说明的事件行为。  
  
    -   左键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   右键单击：引发任何单击事件  
  
    -   左键的双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>;<xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   右键双击：引发任何单击事件  
  
-   <xref:System.Windows.Forms.TextBox><xref:System.Windows.Forms.RichTextBox>， <xref:System.Windows.Forms.ListBox>， <xref:System.Windows.Forms.MaskedTextBox>，和<xref:System.Windows.Forms.CheckedListBox>控件  
  
    > [!NOTE]
    >  当用户单击这些控件内的任意位置时，将发生稍后详细说明的事件行为。  
  
    -   左键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   右键单击：引发任何单击事件  
  
    -   左键的双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>， <xref:System.Windows.Forms.Control.DoubleClick>， <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   右键双击：引发任何单击事件  
  
-   <xref:System.Windows.Forms.ListView> 控件  
  
    > [!NOTE]
    >  仅当用户单击 <xref:System.Windows.Forms.ListView> 控件中的项时，才会发生稍后详细说明的事件行为。 单击该控件上其他任意位置不会引发任何事件。 除了稍后说明的事件外，还有 <xref:System.Windows.Forms.ListView.BeforeLabelEdit> 和 <xref:System.Windows.Forms.ListView.AfterLabelEdit> 事件，如果想要对 <xref:System.Windows.Forms.ListView> 控件进行验证，你可能会对这些事件感兴趣。  
  
    -   左键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   右键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   左键的双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>;<xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   右键双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>;<xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView> 控件  
  
    > [!NOTE]
    >  仅当用户单击 <xref:System.Windows.Forms.TreeView> 控件中的项或项的右侧时，才会发生稍后详细说明的事件行为。 单击该控件上其他任意位置不会引发任何事件。 除了稍后说明的事件，还有 <xref:System.Windows.Forms.TreeView.BeforeCheck>、<xref:System.Windows.Forms.TreeView.BeforeSelect>、<xref:System.Windows.Forms.TreeView.BeforeLabelEdit>、<xref:System.Windows.Forms.TreeView.AfterSelect>、<xref:System.Windows.Forms.TreeView.AfterCheck> 和 <xref:System.Windows.Forms.TreeView.AfterLabelEdit> 事件，如果想要对 <xref:System.Windows.Forms.TreeView> 控件进行验证，你可能会对这些事件感兴趣。  
  
    -   左键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   右键单击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   左键的双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>;<xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   右键双击： <xref:System.Windows.Forms.Control.Click>， <xref:System.Windows.Forms.Control.MouseClick>;<xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>切换控件的绘制行为  
 切换控件（如派生自 <xref:System.Windows.Forms.ButtonBase> 类的控件）具有独特的绘制行为和鼠标单击事件：  
  
1.  用户按下鼠标按钮。  
  
2.  控件以按下状态进行绘制。  
  
3.  引发 <xref:System.Windows.Forms.Control.MouseDown> 事件。  
  
4.  用户释放鼠标按钮。  
  
5.  控件以引发状态进行绘制。  
  
6.  引发 <xref:System.Windows.Forms.Control.Click> 事件。  
  
7.  引发 <xref:System.Windows.Forms.Control.MouseClick> 事件。  
  
8.  引发 <xref:System.Windows.Forms.Control.MouseUp> 事件。  
  
    > [!NOTE]
    >  如果用户在鼠标按钮处于按下状态时将指针移出切换控件（例如在鼠标按下时将鼠标从 <xref:System.Windows.Forms.Button> 控件移出），那么切换控件将以引发状态进行绘制，并且只发生 <xref:System.Windows.Forms.Control.MouseUp> 事件。 在这种情况下，将不会发生 <xref:System.Windows.Forms.Control.Click> 或 <xref:System.Windows.Forms.Control.MouseClick> 事件。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体应用程序中的鼠标输入](mouse-input-in-a-windows-forms-application.md)
