---
title: 演练：布局 Windows 窗体控件与 Padding、 Margins 和 AutoSize 属性
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
ms.openlocfilehash: ca5f968364cd768b708616a867baee49775ca611
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708426"
---
# <a name="walkthrough-laying-out-windows-forms-controls-with-padding-margins-and-the-autosize-property"></a>演练：布局 Windows 窗体控件与 Padding、 Margins 和 AutoSize 属性
在窗体上精确地放置控件对于许多应用程序而言是高优先级。 **Windows 窗体设计器**为你提供许多布局工具实现此目的。 三个最重要的是<xref:System.Windows.Forms.Control.Margin%2A>， <xref:System.Windows.Forms.Control.Padding%2A>，和<xref:System.Windows.Forms.Control.AutoSize%2A>是存在于所有 Windows 窗体控件上的属性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 属性定义控件周围的空间，该空间使其他控件与该控件的边框保持指定的距离。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 属性定义控件内部的空间，该空间使控件的内容（例如，其 <xref:System.Windows.Forms.Control.Text%2A> 属性的值）与该控件的边框保持指定的距离。  
  
 下图显示控件上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 属性。  
  
 ![填充和边距的 Windows 窗体控件](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A>属性告诉控件对其内容自动调整大小。 它将调整自身大小要小于其原始值<xref:System.Windows.Forms.Control.Size%2A>属性，它将体现的值及其<xref:System.Windows.Forms.Control.Padding%2A>属性。  
  
 本演练涉及以下任务：  
  
-   创建 Windows 窗体项目  
  
-   边距设置为您的控件  
  
-   设置控件的填充  
  
-   自动调整控件大小  
  
 完成上述操作后，你将会了解这些重要布局功能所发挥的作用。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，你将需要：  
  
-   若要能够创建和安装 Visual Studio 的计算机上运行 Windows 窗体应用程序项目的足够权限。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建项目并设置窗体。  
  
#### <a name="to-create-the-project"></a>要创建项目  
  
1.  创建**Windows 应用程序**名为项目`LayoutExample`。 有关详细信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)。  
  
2.  选择中的窗体**Windows 窗体设计器**。  
  
## <a name="setting-margins-for-your-controls"></a>边距设置为您的控件  
 可以使用在控件之间设置的默认距离<xref:System.Windows.Forms.Control.Margin%2A>属性。 时将控件移到另一个控件得足够近，你将看到显示了两个控件的边距的对齐线。 要移动的控件还将对齐到定义的边距的距离。  
  
#### <a name="to-arrange-controls-on-your-form-using-the-margin-property"></a>若要在你使用的 Margin 属性的窗体上排列控件  
  
1.  将两个<xref:System.Windows.Forms.Button>控件从**工具箱**拖动到窗体。  
  
2.  选择其中一个<xref:System.Windows.Forms.Button>控制并将其移近另一个，直到它们几乎触摸。  
  
     观察它们之间出现对齐线。 此距离是两个控件的总和<xref:System.Windows.Forms.Control.Margin%2A>值。 控件要移动此距离处对齐。 有关详细信息，请参阅[演练：在 Windows 上排列控件窗体使用对齐线](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
3.  更改<xref:System.Windows.Forms.Control.Margin%2A>之一的展开的控件的属性<xref:System.Windows.Forms.Control.Margin%2A>中的条目**属性**窗口和设置<xref:System.Windows.Forms.Padding.All%2A>属性设置为 20。  
  
4.  选择其中一个<xref:System.Windows.Forms.Button>控制并将其移近另。  
  
     对齐线定义的边距值之和的长度，并该控件从其他控件对齐更远的距离。  
  
5.  更改<xref:System.Windows.Forms.Control.Margin%2A>展开所选控件的属性<xref:System.Windows.Forms.Control.Margin%2A>中的条目**属性**窗口和设置<xref:System.Windows.Forms.Padding.Top%2A>属性设置为 5。  
  
6.  移动其他控件的下方所选的控件，并观察对齐线是较短。 左侧的另一个控件移动所选的控件，并观察对齐线将保留在步骤 4 中观察到的值。  
  
7.  您可以将每个的方面<xref:System.Windows.Forms.Control.Margin%2A>属性， <xref:System.Windows.Forms.Padding.Left%2A>， <xref:System.Windows.Forms.Padding.Top%2A>， <xref:System.Windows.Forms.Padding.Right%2A>， <xref:System.Windows.Forms.Padding.Bottom%2A>、 到不同的值，也可以将其设置为相同的值与所有<xref:System.Windows.Forms.Padding.All%2A>属性。  
  
## <a name="setting-padding-for-your-controls"></a>设置控件的填充  
 若要实现应用程序所需的精确布局，您的控件通常将包含子控件。 当你想要指定子控件的边框的邻近到父控件的边框时，使用父控件的<xref:System.Windows.Forms.Control.Padding%2A>属性结合使用的子控件的<xref:System.Windows.Forms.Control.Margin%2A>属性。 <xref:System.Windows.Forms.Control.Padding%2A>属性还用来控制控件的内容的临近程度 (例如，<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Text%2A>属性) 为其边界。  
  
#### <a name="to-arrange-controls-on-your-form-using-padding"></a>若要在使用填充窗体上排列控件  
  
1.  从 <xref:System.Windows.Forms.Button> “工具箱” **将** 控件拖到你的窗体上。  
  
2.  将 <xref:System.Windows.Forms.Button> 控件的 <xref:System.Windows.Forms.Control.AutoSize%2A> 属性值更改为 `true`。  
  
3.  更改<xref:System.Windows.Forms.Control.Padding%2A>展开属性<xref:System.Windows.Forms.Control.Padding%2A>中的条目**属性**窗口和设置<xref:System.Windows.Forms.Padding.All%2A>属性设置为 5。  
  
     控件扩展以提供新的填充的空间。  
  
4.  从 <xref:System.Windows.Forms.GroupBox> “工具箱” **将** 控件拖到你的窗体上。 拖动<xref:System.Windows.Forms.Button>控件从**工具箱**到<xref:System.Windows.Forms.GroupBox>控件。 位置<xref:System.Windows.Forms.Button>控件使其与的右下角对齐<xref:System.Windows.Forms.GroupBox>控件。  
  
     观察显示为线对齐<xref:System.Windows.Forms.Button>控件接近下边框和右边框的<xref:System.Windows.Forms.GroupBox>控件。 这些对齐线对应于<xref:System.Windows.Forms.Control.Margin%2A>属性的<xref:System.Windows.Forms.Button>。  
  
5.  更改<xref:System.Windows.Forms.GroupBox>控件的<xref:System.Windows.Forms.Control.Padding%2A>展开属性<xref:System.Windows.Forms.Control.Padding%2A>中的条目**属性**窗口和设置<xref:System.Windows.Forms.Padding.All%2A>属性设置为 20。  
  
6.  选择<xref:System.Windows.Forms.Button>内控制<xref:System.Windows.Forms.GroupBox>控件并将它移向的中心<xref:System.Windows.Forms.GroupBox>。  
  
     对齐线显示在更大的距离与的边框<xref:System.Windows.Forms.GroupBox>控件。 此距离是总和<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Margin%2A>属性和<xref:System.Windows.Forms.GroupBox>控件的<xref:System.Windows.Forms.Control.Padding%2A>属性。  
  
## <a name="automatically-sizing-your-controls"></a>自动调整控件大小  
 在某些应用程序，控件的大小不会相同在运行时在设计时一样。 文本<xref:System.Windows.Forms.Button>控件，例如，可能来自一个数据库，并将无法预先知道它的长度。  
  
 当<xref:System.Windows.Forms.Control.AutoSize%2A>属性设置为`true`，控件将自行对其内容。 有关详细信息，请参阅[AutoSize 属性概述](autosize-property-overview.md)。  
  
#### <a name="to-arrange-controls-on-your-form-using-the-autosize-property"></a>若要在使用 AutoSize 属性在窗体上排列控件  
  
1.  从 <xref:System.Windows.Forms.Button> “工具箱” **将** 控件拖到你的窗体上。  
  
2.  将 <xref:System.Windows.Forms.Button> 控件的 <xref:System.Windows.Forms.Control.AutoSize%2A> 属性值更改为 `true`。  
  
3.  更改<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Text%2A>属性设置为"**其 Text 属性的长字符串，该按钮才**。"  
  
     当您提交更改时<xref:System.Windows.Forms.Button>控件自行调整大小以适应新的文本。  
  
4.  将另一个<xref:System.Windows.Forms.Button>控件从**工具箱**拖动到窗体。  
  
5.  更改<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Text%2A>属性设置为"**其 Text 属性的长字符串，该按钮才。**"  
  
     当您提交更改时<xref:System.Windows.Forms.Button>控件不会调整自身大小，并由该控件的右边缘剪裁文本。  
  
6.  更改<xref:System.Windows.Forms.Control.Padding%2A>展开属性<xref:System.Windows.Forms.Control.Padding%2A>中的条目**属性**窗口和设置<xref:System.Windows.Forms.Padding.All%2A>属性设置为 5。  
  
     在控件的内部文本被截断所有四个边。  
  
7.  更改<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.AutoSize%2A>属性设置为`true`。  
  
     <xref:System.Windows.Forms.Button>控件自行调整大小以容纳整个字符串。 此外，将填充添加鼠标按钮，从而导致<xref:System.Windows.Forms.Button>要展开所有四个方向中的控件。  
  
8.  从 <xref:System.Windows.Forms.Button> “工具箱” **将** 控件拖到你的窗体上。 将其定位在窗体右下角附近。  
  
9. 将 <xref:System.Windows.Forms.Button> 控件的 <xref:System.Windows.Forms.Control.AutoSize%2A> 属性值更改为 `true`。  
  
10. 设置<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Anchor%2A>属性设置为<xref:System.Windows.Forms.AnchorStyles.Right>， <xref:System.Windows.Forms.AnchorStyles.Bottom>。  
  
11. 更改<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Text%2A>属性设置为"**其 Text 属性的长字符串，该按钮才。**"  
  
     当您提交更改时<xref:System.Windows.Forms.Button>控件调整自身大小朝向左侧。 一般情况下，自动调整大小将增加相反的方向中的控件的大小及其<xref:System.Windows.Forms.Control.Anchor%2A>属性设置。  
  
## <a name="autosize-and-autosizemode-properties"></a>AutoSize 和 AutoSizeMode 属性  
 某些控件支持`AutoSizeMode`属性，这将使您更加精细地控制控件的自动调整大小行为。  
  
#### <a name="to-use-the-autosizemode-property"></a>若要使用 AutoSizeMode 属性  
  
1.  从 <xref:System.Windows.Forms.Panel> “工具箱” **将** 控件拖到你的窗体上。  
  
2.  设置的值<xref:System.Windows.Forms.Panel>控件的<xref:System.Windows.Forms.Control.AutoSize%2A>属性设置为`true`。  
  
3.  拖动<xref:System.Windows.Forms.Button>控件从**工具箱**到<xref:System.Windows.Forms.Panel>控件。  
  
4.  位置<xref:System.Windows.Forms.Button>控件的右下角附近<xref:System.Windows.Forms.Panel>控件。  
  
5.  选择<xref:System.Windows.Forms.Panel>控件并抓住右下角调整大小控点。 重设大小<xref:System.Windows.Forms.Panel>控件，使其更大和变小。  
  
    > [!NOTE]
    >  你可以自由地调整大小<xref:System.Windows.Forms.Panel>控件，但您不能将其大小小于的位置<xref:System.Windows.Forms.Button>控件的右下角。 默认值指定了此行为`AutoSizeMode`属性，它是<xref:System.Windows.Forms.AutoSizeMode.GrowOnly>。  
  
6.  设置的值<xref:System.Windows.Forms.Panel>控件的`AutoSizeMode`属性设置为<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>。  
  
     <xref:System.Windows.Forms.Panel>控件自行调整大小以环绕<xref:System.Windows.Forms.Button>控件。 不能调整大小<xref:System.Windows.Forms.Panel>控件。  
  
7.  拖动<xref:System.Windows.Forms.Button>控件的左上角向<xref:System.Windows.Forms.Panel>控件。  
  
     <xref:System.Windows.Forms.Panel>控件的大小调整为<xref:System.Windows.Forms.Button>控件的新位置。  
  
## <a name="next-steps"></a>后续步骤  
 有许多其他布局功能，用于在 Windows 窗体应用程序排列控件。 下面是可以尝试一些组合：  
  
-   生成窗体使用<xref:System.Windows.Forms.TableLayoutPanel>控件。 有关详细信息，请参阅[演练：使用 TableLayoutPanel 的 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。 请尝试更改的值<xref:System.Windows.Forms.TableLayoutPanel>控件的<xref:System.Windows.Forms.Control.Padding%2A>属性，并将<xref:System.Windows.Forms.Control.Margin%2A>上子控件的属性。  
  
-   请尝试相同的试验使用<xref:System.Windows.Forms.FlowLayoutPanel>控件。 有关详细信息，请参阅[演练：使用 FlowLayoutPanel 的 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。  
  
-   通过停靠子控件中的实验<xref:System.Windows.Forms.Panel>控件。 <xref:System.Windows.Forms.Control.Padding%2A>属性是的更多常规实现<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>属性，并且可以使自己这种情况，通过将子控件放入<xref:System.Windows.Forms.Panel>控件和设置子控件的<xref:System.Windows.Forms.Control.Dock%2A>属性设置为<xref:System.Windows.Forms.DockStyle.Fill>. 设置<xref:System.Windows.Forms.Panel>控件的<xref:System.Windows.Forms.Control.Padding%2A>到各种值并记下影响的属性。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize 属性概述](autosize-property-overview.md)
- [演练：使用 TableLayoutPanel 的 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [演练：使用 FlowLayoutPanel 的 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [演练：使用对齐线的 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
