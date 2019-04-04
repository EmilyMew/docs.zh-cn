---
title: 演练：承载 WPF 复合控件在 Windows 窗体中
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: d38a9c67edb5df89554e9e02274410a825b3384b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654544"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>演练：承载 WPF 复合控件在 Windows 窗体中
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了用于创建应用程序的丰富环境。 但是，当您有大量投入时[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]代码，它可以更有效地扩展现有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]应用程序与[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]而不是从头开始重新编写。 常见情况是你想要嵌入其中一个或多个控件实现的与[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在 Windows 窗体应用程序中。 有关自定义 WPF 控件的详细信息，请参阅[控件自定义](../controls/control-customization.md)。  
  
 本演练将引导你通过应用程序承载[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件以在 Windows 窗体应用程序中执行数据输入。 复合控件打包在一个 DLL 中。 此常规步骤可扩展到更复杂的应用程序和控件。 本演练旨在几乎完全相同的外观和功能到[演练：在 WPF 中承载 Windows 窗体复合控件](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)。 主要区别在于承载方案是相反的。  
  
 本演练分为两个部分。 第一部分简要介绍的实现[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件。 第二个部分详细讨论了如何承载 Windows 窗体应用程序中的复合控件、 接收来自控件的事件和访问的某些控件的属性。  
  
 本演练涉及以下任务：  
  
-   实现 WPF 复合控件。  
  
-   实现 Windows 窗体主机应用程序。  
  
 在本演练中所涉及任务的完整代码列表，请参阅[承载 WPF 复合控件在 Windows 窗体示例](https://go.microsoft.com/fwlink/?LinkID=159996)。  
  
## <a name="prerequisites"></a>系统必备  

若要完成本演练，必须具有 Visual Studio。  
  
## <a name="implementing-the-wpf-composite-control"></a>实现 WPF 复合控件  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]此示例中使用的复合控件是一种简单的数据输入形式，采用用户的名称和地址。 当用户单击两个按钮的其中一个以指示任务已完成时，该控件会引发将该信息返回给主机的自定义事件。 下图显示呈现的控件。 

 下图显示了 WPF 复合控件： 

  
 ![显示简单的 WPF 控件的屏幕截图。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>创建项目  
 启动项目：  
  
1.  启动[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，并打开**新建项目**对话框。  
  
2.  在 Visual C# 和 Windows 类别中，选择**WPF 用户控件库**模板。  
  
3.  将新项目命名为 `MyControls`。  
  
4.  对于位置，指定可以方便命名的顶层文件夹，如`WindowsFormsHostingWpfControl`。 随后，将主机应用程序放在此文件夹中。  
  
5.  单击“确定”，创建项目。 默认项目包含名为的单个控件`UserControl1`。  
  
6.  在解决方案资源管理器，重命名`UserControl1`到`MyControl1`。  
  
 项目应具有对以下系统 DLL 的引用。 如果默认未包含其中任何 DLL，请将它们添加到项目中。  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   系统  
  
-   WindowsBase  
  
### <a name="creating-the-user-interface"></a>创建用户界面  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]复合控件实现与[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 复合控件[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]包含五个<xref:System.Windows.Controls.TextBox>元素。 每个<xref:System.Windows.Controls.TextBox>元素都有一个关联<xref:System.Windows.Controls.TextBlock>充当标签的元素。 有两个<xref:System.Windows.Controls.Button>在底部，元素**确定**并**取消**。 当用户单击任一按钮时，该控件会引发将信息返回给主机的自定义事件。  
  
#### <a name="basic-layout"></a>基本布局  
 各种[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素包含在<xref:System.Windows.Controls.Grid>元素。 可以使用<xref:System.Windows.Controls.Grid>要排列的复合内容控制在很大程度相同方式使用`Table`中 HTML 元素。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 还有<xref:System.Windows.Documents.Table>元素，但<xref:System.Windows.Controls.Grid>更轻便、 更好地适用于简单的布局任务。  
  
 以下 XAML 演示基本布局。 此 XAML 通过指定的列数定义的控件的整体结构和中的行<xref:System.Windows.Controls.Grid>元素。  
  
 在 MyControl1.xaml 中，将现有 XAML 替换为以下 XAML。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>向 Grid 添加 TextBlock 和 TextBox 元素  
 您将放[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]通过设置元素的网格中的元素<xref:System.Windows.Controls.Grid.RowProperty>和<xref:System.Windows.Controls.Grid.ColumnProperty>属性到相应的行和列号。 请记住行号和列号是从零开始的。 你可以通过设置跨多个列的元素及其<xref:System.Windows.Controls.Grid.ColumnSpanProperty>属性。 有关详细信息<xref:System.Windows.Controls.Grid>元素，请参阅[创建网格元素](../controls/how-to-create-a-grid-element.md)。  
  
 以下 XAML 演示复合控件<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBlock>元素及其<xref:System.Windows.Controls.Grid.RowProperty>和<xref:System.Windows.Controls.Grid.ColumnProperty>属性，它们被设置为将元素正确放置在网格中。  
  
 在 MyControl1.xaml 中，添加以下 XAML 中的<xref:System.Windows.Controls.Grid>元素。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>设置 UI 元素的样式  
 数据输入窗体上的许多元素外观相似，这意味着它们对于其若干属性具有相同的设置。 而不是单独设置每个元素的特性，使用上一个 XAML<xref:System.Windows.Style>元素可定义为类的元素的标准属性设置。 这种方法可以降低控件的复杂性，并使你能够通过单个样式特性更改多个元素的外观。  
  
 <xref:System.Windows.Style>元素包含在<xref:System.Windows.Controls.Grid>元素的<xref:System.Windows.FrameworkElement.Resources%2A>属性，因此它们可以由该控件中的所有元素。 如果命名了某样式，您将其应用于元素通过添加<xref:System.Windows.Style>元素设置为该样式的名称。 未命名的样式将成为该元素的默认样式。 有关详细信息[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]样式，请参阅[样式和模板化](../controls/styling-and-templating.md)。  
  
 下面的 XAML 演示<xref:System.Windows.Style>复合控件元素。 若要查看样式如何应用于元素，请参阅前一个 XAML。 例如上, 一次<xref:System.Windows.Controls.TextBlock>元素具有`inlineText`样式和最后一个<xref:System.Windows.Controls.TextBox>元素使用的默认样式。  
  
 在 MyControl1.xaml 中，添加以下 XAML 之后<xref:System.Windows.Controls.Grid>开始元素。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>添加“确定”和“取消”按钮  
 复合控件上的最后一个元素是**确定**并**取消**<xref:System.Windows.Controls.Button>元素，它们占用的最后一行的前两个列<xref:System.Windows.Controls.Grid>。 这些元素使用常见的事件处理程序`ButtonClicked`，默认值和<xref:System.Windows.Controls.Button>上一个 XAML 中定义的样式。  
  
 在 MyControl1.xaml 中，最后一个后面添加以下 XAML<xref:System.Windows.Controls.TextBox>元素。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]复合控件的一部分现已完成。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>实现代码隐藏文件  
 代码隐藏文件 MyControl1.xaml.cs 实现三个基本任务：
  
1.  处理用户单击其中一个按钮时发生的事件。  
  
2.  检索从数据<xref:System.Windows.Controls.TextBox>元素，并将它们打包在一个自定义事件参数对象。  
  
3.  引发自定义`OnButtonClick`事件，通知主机用户已完成，并将数据传递回主机。  
  
 该控件还公开多个可用来更改外观的颜色和字体属性。 与不同<xref:System.Windows.Forms.Integration.WindowsFormsHost>类，该类用于承载 Windows 窗体控件<xref:System.Windows.Forms.Integration.ElementHost>类公开控件的<xref:System.Windows.Controls.Panel.Background%2A>只属性。 若要维护此代码示例和讨论的示例中之间的相似性[演练：承载 Windows 窗体复合控件在 WPF 中](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)，该控件直接公开其余属性。  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>代码隐藏文件的基本结构  
 代码隐藏文件包含的单个命名空间，由`MyControls`，其中包含两个类`MyControl1`和`MyControlEventArgs`。  
  
```  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
```  
  
 第一个类`MyControl1`，是一个包含实现的功能的代码的分部类[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]MyControl1.xaml 中定义。 当解析 MyControl1.xaml 中时，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]转换为相同的分部类和两个分部类会合并形成编译的控件。 出于此原因，代码隐藏文件中的类名必须与分配给 MyControl1.xaml 的类名相匹配，并且它必须继承自控件的根元素。 第二个类， `MyControlEventArgs`，是一个事件参数类，用于将数据发送回主机。  
  
 打开 MyControl1.xaml.cs。 更改现有的类声明，以便它具有以下名称并继承<xref:System.Windows.Controls.Grid>。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>初始化控件  
 下面的代码实现几个基本任务：  
  
-   声明一个私有事件`OnButtonClick`，和及其关联的委托`MyControlEventHandler`。  
  
-   创建几个存储用户数据的私有全局变量。 此数据通过相应的属性公开。  
  
-   实现一个处理程序`Init`，为控件的<xref:System.Windows.FrameworkElement.Loaded>事件。 此处理程序通过向全局变量分配 MyControl1.xaml 中定义的值来对它们进行初始化。 若要执行此操作，它使用<xref:System.Windows.FrameworkElement.Name%2A>分配给典型<xref:System.Windows.Controls.TextBlock>元素， `nameLabel`，以访问该元素的属性设置。  
  
 删除现有的构造函数并将以下代码添加到你`MyControl1`类。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>处理按钮的单击事件  
 用户指示数据输入任务已完成通过单击**确定**按钮或**取消**按钮。 这两个按钮都使用相同<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件处理程序`ButtonClicked`。 这两个按钮都具有名称，`btnOK`或`btnCancel`，这样，要确定通过检查的值被单击的按钮的处理程序`sender`参数。 该处理程序执行以下任务：  
  
-   创建`MyControlEventArgs`对象，其中包含从数据<xref:System.Windows.Controls.TextBox>元素。  
  
-   如果用户单击**取消**按钮，集`MyControlEventArgs`对象的`IsOK`属性设置为`false`。  
  
-   引发`OnButtonClick`事件以向主机指示用户已完成，并且传回所收集的数据。  
  
 将以下代码添加到您`MyControl1`类后,`Init`方法。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>创建属性  
 类的其余部分只是公开对应于前面所述的全局变量的属性。 当属性更改时，set 访问器会通过更改对应的元素属性并更新基础全局变量来修改控件的外观。  
  
 将以下代码添加到你`MyControl1`类。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>将数据发送回主机  
 在文件中的最后一个组件是`MyControlEventArgs`类，该类用于将收集的数据发送回主机。  
  
 将以下代码添加到你`MyControls`命名空间。 该实现非常简单明了，因而不再进一步讨论。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 生成解决方案。 生成将产生一个名为 MyControls.dll 的 DLL。  
  
<a name="winforms_host_section"></a>   
## <a name="implementing-the-windows-forms-host-application"></a>实现 Windows 窗体主机应用程序  
 Windows 窗体承载应用程序使用<xref:System.Windows.Forms.Integration.ElementHost>对象承载[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件。 该应用程序处理`OnButtonClick`事件以接收来自复合控件的数据。 该应用程序还具有一组可用于修改控件外观的选项按钮。 下图显示应用程序。  

下图显示了在 Windows 窗体应用程序中承载的 WPF 复合控件"  

 ![显示 Windows 窗体承载 Avalon 控件的 Scteenshot。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>创建项目  
 启动项目：  
  
1.  启动[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，并打开**新建项目**对话框。  
  
2.  在 Visual C# 和 Windows 类别中，选择**Windows 窗体应用程序**模板。  
  
3.  将新项目命名为 `WFHost`。  
  
4.  对于位置，指定包含 MyControls 项目的同一顶层文件夹。  
  
5.  单击“确定”，创建项目。  
  
 此外需要添加对包含的 DLL 的引用`MyControl1`和其他程序集。  
  
1.  右键单击解决方案资源管理器中的项目名称并选择**添加引用**。  
  
2.  单击**浏览**选项卡，然后浏览到包含 MyControls.dll 的文件夹。 在本演练中，此文件夹位于 MyControls\bin\Debug。  
  
3.  选择 MyControls.dll，然后依次**确定**。  
  
4.  添加对下列程序集的引用。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>实现应用程序的用户界面  
 Windows 窗体应用程序的 UI 包含若干个与 WPF 复合控件进行交互的控件。  
  
1.  在 Windows 窗体设计器中打开 Form1。  
  
2.  放大窗体以适应控件。  
  
3.  在窗体的右上角，添加<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>控件以容纳[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件。  
  
4.  以下代码添加到<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>到窗体控件。  
  
    |名称|Text|  
    |----------|----------|  
    |groupBox1|背景色|  
    |groupBox2|前景色|  
    |groupBox3|字号|  
    |groupBox4|字体系列|  
    |groupBox5|字形|  
    |groupBox6|字体粗细|  
    |groupBox7|来自控件的数据|  
  
5.  添加以下<xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>控件添加到<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>控件。  
  
    |GroupBox|名称|Text|  
    |--------------|----------|----------|  
    |groupBox1|radioBackgroundOriginal|原始|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|原始|  
    |groupBox2|radioForegroundRed|红色|  
    |groupBox2|radioForegroundYellow|黄色|  
    |groupBox3|radioSizeOriginal|原始|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|原始|  
    |groupBox4|radioFamilyTimes|宋体, Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|普通|  
    |groupBox5|radioStyleItalic|斜体|  
    |groupBox6|radioWeightOriginal|原始|  
    |groupBox6|radioWeightBold|粗体|  
  
6.  添加以下<xref:System.Windows.Forms.Label?displayProperty=nameWithType>到最后一个控制<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>。 这些控件显示返回的数据[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件。  
  
    |GroupBox|名称|文本|  
    |--------------|----------|----------|  
    |groupBox7|lblName|姓名:|  
    |groupBox7|lblAddress|街道地址:|  
    |groupBox7|lblCity|市/县:|  
    |groupBox7|lblState|省/自治区/直辖市:|  
    |groupBox7|lblZip|邮政编码:|  
  
### <a name="initializing-the-form"></a>初始化窗体  
 通常在窗体的实现承载代码<xref:System.Windows.Forms.Form.Load>事件处理程序。 下面的代码演示<xref:System.Windows.Forms.Form.Load>事件处理程序中，处理程序[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件的<xref:System.Windows.FrameworkElement.Loaded>事件，以及更高版本使用的几个全局变量的声明。  
  
 在 Windows 窗体设计器中，双击窗体创建<xref:System.Windows.Forms.Form.Load>事件处理程序。 在 Form1.cs 顶部，添加以下`using`语句。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 现有内容替换为`Form1`用下面的代码的类。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 `Form1_Load`方法在前面的代码演示了托管的一般过程[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控件：  
  
1.  创建一个新<xref:System.Windows.Forms.Integration.ElementHost>对象。  
  
2.  设置控件的<xref:System.Windows.Forms.Control.Dock%2A>属性设置为<xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>。  
  
3.  添加<xref:System.Windows.Forms.Integration.ElementHost>控制对<xref:System.Windows.Forms.Panel>控件的<xref:System.Windows.Forms.Control.Controls%2A>集合。  
  
4.  创建的实例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控件。  
  
5.  通过将分配到控件中承载复合控件在窗体上的<xref:System.Windows.Forms.Integration.ElementHost>控件的<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>属性。  
  
 中的其余两行将`Form1_Load`方法附加到两个控件事件处理程序：  
  
-   `OnButtonClick` 是一个自定义事件，当用户单击由复合控件激发**确定**或**取消**按钮。 处理该事件可获取用户的响应并收集用户指定的任何数据。  
  
-   <xref:System.Windows.FrameworkElement.Loaded> 是一个标准事件引发的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制时完全加载。 此处使用该事件是因为本示例需要使用控件中的属性初始化几个全局变量。 在窗体的时间<xref:System.Windows.Forms.Form.Load>事件，该控件不是完全加载，并且这些值仍设置为`null`。 你需要等到该控件<xref:System.Windows.FrameworkElement.Loaded>事件发生之前可以访问这些属性。  
  
 <xref:System.Windows.FrameworkElement.Loaded>事件处理程序在前面的代码所示。 `OnButtonClick`中下一节讨论处理程序。  
  
### <a name="handling-onbuttonclick"></a>处理 OnButtonClick  
 `OnButtonClick`事件发生在用户单击时**确定**或**取消**按钮。  
  
 事件处理程序将检查事件参数`IsOK`字段，以确定被单击的按钮。 `lbl`*数据*变量对应于<xref:System.Windows.Forms.Label>前面讨论过的控件。 如果用户单击**确定**按钮，从控件的数据<xref:System.Windows.Controls.TextBox>控件分配给对应<xref:System.Windows.Forms.Label>控件。 如果用户单击**取消**，则<xref:System.Windows.Forms.Label.Text%2A>值设置为默认值的字符串。  
  
 添加下面的按钮单击事件处理程序代码与`Form1`类。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 生成并运行应用程序。 在 WPF 复合控件中添加一些文本，然后单击**确定**。 文本将显示在标签中。 此时，尚未添加代码来处理单选按钮。  
  
### <a name="modifying-the-appearance-of-the-control"></a>修改控件的外观  
 <xref:System.Windows.Forms.RadioButton>窗体控件将使用户能够更改[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]复合控件的前景色和背景色以及若干字体属性。 背景色由<xref:System.Windows.Forms.Integration.ElementHost>对象。 其余属性作为控件的自定义属性公开。  
  
 双击每个<xref:System.Windows.Forms.RadioButton>要创建的窗体上控件<xref:System.Windows.Forms.RadioButton.CheckedChanged>事件处理程序。 替换为<xref:System.Windows.Forms.RadioButton.CheckedChanged>事件处理程序替换下面的代码。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 生成并运行应用程序。 单击不同的单选按钮来查看在 WPF 复合控件上的效果。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中设计 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [演练：承载在 WPF 中的 Windows 窗体复合控件](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [演练：承载 3-D WPF 复合控件在 Windows 窗体中](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
