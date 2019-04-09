---
title: 根据功能列出的 Windows 窗体控件
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115474"
---
# <a name="windows-forms-controls-by-function"></a>根据功能列出的 Windows 窗体控件
Windows 窗体还提供控件和组件执行的许多功能。 下表列出了 Windows 窗体控件和组件根据常规函数。 此外，多个控件存在的具有相同的功能时，与它所取代的控件中还要注意： 列出推荐的控件。 在随后的一个单独的表中，使用它们的建议替换项列出被取代的控件。  
  
> [!NOTE]
>  下表未列出的每个控件或组件可在 Windows 窗体;有关更全面的列表，请参阅[Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>建议的控件和组件函数  
  
|函数|控件|描述|  
|--------------|-------------|-----------------|  
|数据显示|<xref:System.Windows.Forms.DataGridView> 控件|<xref:System.Windows.Forms.DataGridView>控件提供可自定义的表，用于显示数据。 <xref:System.Windows.Forms.DataGridView>类允许自定义的单元格、 行、 列和边框。 **注意：** <xref:System.Windows.Forms.DataGridView>控件提供了许多的基本和高级功能，中缺少<xref:System.Windows.Forms.DataGrid>控件。 有关详细信息，请参阅[差异 Windows 窗体 DataGridView 控件与之间的 DataGrid 控件](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|数据绑定和导航|<xref:System.Windows.Forms.BindingSource> 组件|当前项管理、 更改通知和其他服务，从而简化了将控件绑定到数据窗体上。|  
||<xref:System.Windows.Forms.BindingNavigator> 控件|提供一个工具栏类型接口用于导航和操作窗体上的数据。|  
|文本编辑|<xref:System.Windows.Forms.TextBox> 控件|显示在设计时，可以在运行时，由用户编辑或以编程方式更改输入的文本。|  
||<xref:System.Windows.Forms.RichTextBox> 控件|启用要使用的纯文本或丰富文本格式 (RTF) 中的格式设置来显示文本。|  
||<xref:System.Windows.Forms.MaskedTextBox> 控件|约束用户输入的格式|  
|（只读） 显示的信息|<xref:System.Windows.Forms.Label> 控件|显示用户无法直接编辑的文本。|  
||<xref:System.Windows.Forms.LinkLabel> 控件|为 Web 样式的链接显示文本，并触发事件时在用户单击特殊文本。 该文本通常是指向另一个窗口或网站的链接。|  
||<xref:System.Windows.Forms.StatusStrip> 控件|显示有关应用程序的当前状态通常在父窗体的底部使用框架的区域信息。|  
||<xref:System.Windows.Forms.ProgressBar> 控件|为用户显示操作的当前进度。|  
|网页上显示|<xref:System.Windows.Forms.WebBrowser> 控件|使用户能够在你的窗体中导航网页。|  
|从列表选择|<xref:System.Windows.Forms.CheckedListBox> 控件|显示可滚动列表的项，每个旁边都有一个复选框。|  
||<xref:System.Windows.Forms.ComboBox> 控件|显示项的下拉列表。|  
||<xref:System.Windows.Forms.DomainUpDown> 控件|显示用户可以滚动浏览使用向上和向下按钮的文本项的列表。|  
||<xref:System.Windows.Forms.ListBox> 控件|显示文本和图形项目 （图标） 的列表。|  
||<xref:System.Windows.Forms.ListView> 控件|一个四个不同的视图中显示项。 视图包括纯文本、 具有小图标的文本、 文本、 带有大图标和详细信息视图。|  
||<xref:System.Windows.Forms.NumericUpDown> 控件|显示用户可以滚动浏览使用向上和向下按钮的数字的列表。|  
||<xref:System.Windows.Forms.TreeView> 控件|显示层次结构可以包含具有可选的复选框或图标的文本的节点对象的集合。|  
|图形显示|<xref:System.Windows.Forms.PictureBox> 控件|在帧中显示图形文件，如位图和图标。|  
|图形存储|<xref:System.Windows.Forms.ImageList> 控件|用作映像的存储库。 <xref:System.Windows.Forms.ImageList> 可重复到下一个应用程序中使用控件以及它们所包含的图像。|  
|值设置|<xref:System.Windows.Forms.CheckBox> 控件|显示一个复选框和文本的标签。 通常用来设置选项。|  
||<xref:System.Windows.Forms.CheckedListBox> 控件|显示可滚动列表的项，每个旁边都有一个复选框。|  
||<xref:System.Windows.Forms.RadioButton> 控件|显示可以打开或关闭的按钮。|  
||<xref:System.Windows.Forms.TrackBar> 控件|允许用户通过移动"thumb"沿刻度的刻度上设置的值。|  
|日期设置|<xref:System.Windows.Forms.DateTimePicker> 控件|显示一个图形日历以允许用户选择日期或时间。|  
||<xref:System.Windows.Forms.MonthCalendar> 控件|显示一个图形日历以允许用户选择日期范围内。|  
|对话框|<xref:System.Windows.Forms.ColorDialog> 控件|显示颜色选取器对话框，允许用户设置的界面元素的颜色。|  
||<xref:System.Windows.Forms.FontDialog> 控件|显示一个对话框，允许用户设置字体和其属性。|  
||<xref:System.Windows.Forms.OpenFileDialog> 控件|显示一个对话框，允许用户导航到并选择一个文件。|  
||<xref:System.Windows.Forms.PrintDialog> 控件|显示一个对话框，允许用户选择打印机并设置其属性。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> 控件|显示一个对话框，显示如何控制<xref:System.Drawing.Printing.PrintDocument>打印时，将显示组件。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> 控件|显示一个对话框，允许用户浏览、 创建，并最终选择的文件夹|  
||<xref:System.Windows.Forms.SaveFileDialog> 控件|显示一个对话框，允许用户保存文件。|  
|菜单控件|<xref:System.Windows.Forms.MenuStrip> 控件|创建自定义菜单。 **注意：** <xref:System.Windows.Forms.MenuStrip>旨在替换<xref:System.Windows.Forms.MainMenu>控件。|  
||<xref:System.Windows.Forms.ContextMenuStrip> 控件|创建自定义上下文菜单。 **注意：** <xref:System.Windows.Forms.ContextMenuStrip>旨在替换<xref:System.Windows.Forms.ContextMenu>控件。|  
|命令|<xref:System.Windows.Forms.Button> 控件|启动、 停止或中断进程。|  
||<xref:System.Windows.Forms.LinkLabel> 控件|为 Web 样式的链接显示文本，并触发事件时在用户单击特殊文本。 该文本通常是指向另一个窗口或网站的链接。|  
||<xref:System.Windows.Forms.NotifyIcon> 控件|表示在后台运行的应用程序在任务栏的状态通知区域中显示的图标。|  
||<xref:System.Windows.Forms.ToolStrip> 控件|创建可包含 Microsoft Windows XP、 Microsoft Office、 Microsoft Internet Explorer 中或自定义外观和感觉，与或而无需主题，和对溢出数据和运行时项重新排序功能的支持的工具栏。 **注意：** <xref:System.Windows.Forms.ToolStrip>控件旨在替换<xref:System.Windows.Forms.ToolBar>控件。|  
|用户帮助|<xref:System.Windows.Forms.HelpProvider> 组件|为控件提供弹出帮助或联机帮助。|  
||<xref:System.Windows.Forms.ToolTip> 组件|提供一个弹出窗口，当用户将指针停留在控件上时显示控件的用途的简要说明。|  
|将其他控件分组|<xref:System.Windows.Forms.Panel> 控件|一组未标记，可滚动的帧上的控件。|  
||<xref:System.Windows.Forms.GroupBox> 控件|组标记，非滚动框架上的控件 （如单选按钮）。|  
||<xref:System.Windows.Forms.TabControl> 控件|提供了用于组织和访问选项卡式的页面分组对象有效。|  
||<xref:System.Windows.Forms.SplitContainer> 控件|提供由可移动条分隔的两个面板。 **注意：** <xref:System.Windows.Forms.SplitContainer>控件旨在替换<xref:System.Windows.Forms.Splitter>控件。|  
||<xref:System.Windows.Forms.TableLayoutPanel> 控件|表示一个面板，它可以在一个由行和列组成的网格中对其内容进行动态布局。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> 控件|表示以水平或垂直方式动态布置其内容的面板。|  
|音频|<xref:System.Media.SoundPlayer> 控件|播放声音中.wav 格式的文件。 可以加载或以异步方式播放声音。|  
  
## <a name="superseded-controls-and-components-by-function"></a>被取代的控件和组件函数  
  
|函数|被取代的控件|推荐的替代|  
|--------------|------------------------|-----------------------------|  
|数据显示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|显示的信息 （只读的控件）|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|菜单控件|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|命令|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|窗体布局|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>请参阅

- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
- [使用 .NET Framework 开发自定义 Windows 窗体控件](developing-custom-windows-forms-controls.md)
