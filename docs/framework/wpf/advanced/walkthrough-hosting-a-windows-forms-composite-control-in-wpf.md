---
title: 演练：承载在 WPF 中的 Windows 窗体复合控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 50d85b74b523c8985bd0d3d407097a4f42cfeb60
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654219"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>演练：承载在 WPF 中的 Windows 窗体复合控件
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了用于创建应用程序的丰富环境。 但是，当您有大量投入时[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]代码，它可以更有效地重复使用至少某些中的代码在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序而不是从头开始重新编写。 最常见的方案是具有现有 Windows 窗体控件。 在某些情况下，你甚至可能无法使用这些控件的源代码。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一个简单的过程中的此类控件承载[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。 例如，可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]对于大多数应用编程，同时承载专用<xref:System.Windows.Forms.DataGridView>控件。  
  
 本演练将指导你逐步承载 Windows 窗体复合控件以执行中的数据输入的应用程序[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。 复合控件打包在一个 DLL 中。 此常规步骤可扩展到更复杂的应用程序和控件。 本演练旨在几乎完全相同的外观和功能到[演练：承载 WPF 复合控件在 Windows 窗体中的](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)。 主要区别在于承载方案是相反的。  
  
 本演练分为两个部分。 第一部分简要介绍 Windows 窗体复合控件的实现。 第二个部分详细讨论如何托管中的复合控件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序，接收来自控件的事件和访问的某些控件的属性。  
  
 本演练涉及以下任务：  
  
-   实现 Windows 窗体复合控件。  
  
-   实现 WPF 主机应用程序。  
  
 在本演练中所涉及任务的完整代码列表，请参阅[承载 Windows 窗体复合控件在 WPF 示例中](https://go.microsoft.com/fwlink/?LinkID=159999)。  
  
## <a name="prerequisites"></a>系统必备  

若要完成本演练，必须具有 Visual Studio。
  
## <a name="implementing-the-windows-forms-composite-control"></a>实现 Windows 窗体复合控件  
 在此示例中使用的 Windows 窗体复合控件是一个简单的数据输入窗体。 此窗体需要用户名和地址，然后使用自定义事件将该信息返回到主机。 下图显示呈现的控件。  

 下图显示了 Windows 窗体复合控件：  

 ![显示简单的 Windows 窗体控件的屏幕截图。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>创建项目  
 启动项目：  
  
1.  启动[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，并打开**新建项目**对话框。  
  
2.  在窗口类别，选择**Windows 窗体控件库**模板。  
  
3.  将新项目命名为 `MyControls`。  
  
4.  对于位置，指定可以方便命名的顶层文件夹，如`WpfHostingWindowsFormsControl`。 随后，将主机应用程序放在此文件夹中。  
  
5.  单击“确定”，创建项目。 默认项目包含名为的单个控件`UserControl1`。  
  
6.  在解决方案资源管理器，重命名`UserControl1`到`MyControl1`。  
  
 项目应具有对以下系统 DLL 的引用。 如果默认不包含其中任何 DLL，则将它们添加到项目中。  
  
-   系统  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>将控件添加到窗体  
 向窗体添加控件：  
  
-   打开`MyControl1`在设计器中。  
  
 添加五个<xref:System.Windows.Forms.Label>及其对应<xref:System.Windows.Forms.TextBox>控件，调整大小和排列方式与其在上图中，在窗体上。 在示例中，<xref:System.Windows.Forms.TextBox>控件命名为：  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 添加两个<xref:System.Windows.Forms.Button>控件标记为**确定**并**取消**。 在此示例中，按钮名称是`btnOK`和`btnCancel`分别。  
  
### <a name="implementing-the-supporting-code"></a>实现支持代码  
 在代码视图中打开窗体。 控件返回到其主机通过引发自定义的收集的数据`OnButtonClick`事件。 数据包含在事件自变量对象中。 以下代码演示事件和委托声明。  
  
 向 `MyControl1` 类添加下面的代码。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs`类包含要返回到主机的信息。

 将以下类添加到窗体中。

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 当用户单击**确定**或**取消**按钮，<xref:System.Windows.Forms.Control.Click>事件处理程序创建`MyControlEventArgs`对象，其中包含数据，并引发`OnButtonClick`事件。 两个处理程序之间的唯一区别是事件自变量的`IsOK`属性。 此属性使主机可以确定单击的按钮。 设置为`true`有关**确定**按钮，并`false`有关**取消**按钮。 以下代码演示两个按钮处理程序。

 向 `MyControl1` 类添加下面的代码。

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>赋予程序集强名称并生成程序集
 此程序集引用的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序，它必须具有强名称。 若要创建强名称，使用 Sn.exe 创建密钥文件并将其添加到你的项目。

1.  打开一个 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示符。 若要执行此操作，请单击**启动**菜单，并选择**所有 Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio 命令提示符**。 这将启动包含自定义环境变量的控制台窗口。

2.  在命令提示符下，使用`cd`命令可以转到你的项目文件夹。

3.  通过运行以下命令生成名为 MyControls.snk 的密钥文件。

    ```
    Sn.exe -k MyControls.snk
    ```

4.  要在项目中包含的密钥文件，右键单击解决方案资源管理器中的项目名称，然后单击**属性**。 在项目设计器中，单击**签名**选项卡上，选择**程序集签名**复选框，然后浏览到你的密钥文件。

5.  生成解决方案。 生成将产生一个名为 MyControls.dll 的 DLL。

## <a name="implementing-the-wpf-host-application"></a>实现 WPF 主机应用程序
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]宿主应用程序使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件来承载`MyControl1`。 该应用程序处理`OnButtonClick`事件以接收来自控件的数据。 它还具有一组选项按钮，您可以更改某些控件的属性从[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。 下图显示已完成的应用程序。

下图显示完整的应用程序，包括控件嵌入在 WPF 应用程序：

 ![显示控件的屏幕截图嵌入在 WPF 页中。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>创建项目
 启动项目：

1.  打开[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然后选择**新建项目**。

2.  在窗口类别，选择**WPF 应用程序**模板。

3.  将新项目命名为 `WpfHost`。

4.  对于位置，指定包含 MyControls 项目的同一顶层文件夹。

5.  单击“确定”，创建项目。

 此外需要添加对包含的 DLL 的引用`MyControl1`和其他程序集。

1.  右键单击解决方案资源管理器中的项目名称并选择**添加引用**。

2.  单击**浏览**选项卡，然后浏览到包含 MyControls.dll 的文件夹。 在本演练中，此文件夹位于 MyControls\bin\Debug。

3.  选择 MyControls.dll，然后依次**确定**。

4.  添加对 WindowsFormsIntegration 程序集，它名为 WindowsFormsIntegration.dll 的引用。

### <a name="implementing-the-basic-layout"></a>实现基本布局
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]的主机在 MainWindow.xaml 中实现应用程序。 此文件包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定义布局，并托管在 Windows 窗体控件的标记。 该应用程序分为三个区域：

-   **控件属性**面板，其中包含一组可用于修改所承载控件的各种属性的选项按钮。

-   **来自控件的数据**面板，其中包含几个<xref:System.Windows.Controls.TextBlock>从承载控件返回显示的数据的元素。

-   所承载控件本身。

 基本布局如下面的 XAML 中所示。 需要的标记到主机`MyControl1`从本示例中，省略了，但将在下文。

 将 MainWindow.xaml 中的 XAML 替换为以下内容。 如果使用的 Visual Basic，更改到类`x:Class="MainWindow"`。

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 第一个<xref:System.Windows.Controls.StackPanel>元素包含多组<xref:System.Windows.Controls.RadioButton>控件，您可以修改所承载控件的各种默认属性。 后跟<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素中，哪些主机`MyControl1`。 最终<xref:System.Windows.Controls.StackPanel>元素包含多个<xref:System.Windows.Controls.TextBlock>元素，用于显示所承载控件返回的数据。 排序的元素和<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>属性设置不存在的空白或扭曲使用嵌入到窗口中承载的控件。

#### <a name="hosting-the-control"></a>承载控件
 上一个 XAML 的以下已编辑的版本重点介绍所需的元素到主机`MyControl1`。

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns`命名空间映射属性将创建对引用`MyControls`包含所承载的控件的命名空间。 此映射使你能够代表`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]作为`<mcl:MyControl1>`。

 XAML 中的两个元素处理承载：

-   `WindowsFormsHost` 表示<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，可用于承载 Windows 窗体控件中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。

-   `mcl:MyControl1`表示`MyControl1`，添加到<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子集合。 因此，此 Windows 窗体控件呈现为一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]窗口中，并且您可以与该控件从该应用程序进行通信。

### <a name="implementing-the-code-behind-file"></a>实现代码隐藏文件
 代码隐藏文件，MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，包含实现的功能的过程性代码[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]前面部分所述。 主要任务有：

-   附加到事件处理程序`MyControl1`的`OnButtonClick`事件。

-   修改的各种属性`MyControl1`根据选项按钮集合的设置方式。

-   显示控件收集的数据。

#### <a name="initializing-the-application"></a>初始化应用程序
 初始化代码包含在窗口的一个事件处理程序<xref:System.Windows.FrameworkElement.Loaded>事件，并将事件处理程序附加到控件的`OnButtonClick`事件。

 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，以下代码添加到`MainWindow`类。

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 因为[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讨论之前添加`MyControl1`到<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子元素集合，可以强制转换<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>若要获取对引用`MyControl1`。 然后可以使用该引用将附加到事件处理程序`OnButtonClick`。

 除了提供对控件本身的引用<xref:System.Windows.Forms.Integration.WindowsFormsHost>公开多个控件的属性，您可以从应用程序操作。 初始化代码将这些值分配给私有全局变量，以供稍后在应用程序中使用。

 以便可以轻松地访问中的类型`MyControls`DLL，添加以下`Imports`或`using`到文件顶部的语句。

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>处理 OnButtonClick 事件
 `MyControl1` 引发`OnButtonClick`事件，当用户单击任一控件的按钮。

 向 `MainWindow` 类添加下面的代码。

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 在文本框中的数据打包到`MyControlEventArgs`对象。 如果用户单击**确定**按钮，事件处理程序中提取数据并将其显示下方的面板中`MyControl1`。

#### <a name="modifying-the-controls-properties"></a>修改控件属性
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素公开多个托管的控件的默认属性。 因此，可以更改空间外观，以更贴合应用程序的样式。 位于左侧面板中的选项按钮组使用户能够修改多个颜色和字体属性。 按钮的每个集具有的处理程序<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，它检测到用户的选项按钮选择和更改控件上的相应属性。

 向 `MainWindow` 类添加下面的代码。

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 生成并运行应用程序。 在 Windows 窗体复合控件中添加一些文本，然后单击**确定**。 文本将显示在标签中。 单击不同的单选按钮查看在控件上的效果。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中设计 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [演练：承载在 WPF 中的 Windows 窗体控件](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [演练：承载 WPF 复合控件在 Windows 窗体中](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
