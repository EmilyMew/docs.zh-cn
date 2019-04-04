---
title: ToolStrip 控件体系结构
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: bede247ca9e1c2c20ffc8fef9fd4fab89aa78453
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654765"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip 控件体系结构
<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>类用于显示工具栏、 状态和菜单项提供一个灵活、 可扩展的系统。 这些类都包含在<xref:System.Windows.Forms>命名空间和它们全部通常具有"ToolStrip"前缀命名 (如<xref:System.Windows.Forms.ToolStripOverflow>) 或带有"带状"后缀 (例如<xref:System.Windows.Forms.MenuStrip>)。  
  
## <a name="toolstrip"></a>ToolStrip  
 下面的主题介绍<xref:System.Windows.Forms.ToolStrip>和从其派生的控件。  
  
 <xref:System.Windows.Forms.ToolStrip> 是的抽象基类<xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.StatusStrip>，和<xref:System.Windows.Forms.ContextMenuStrip>。 下面的对象模型演示<xref:System.Windows.Forms.ToolStrip>继承层次结构。  
  
 ![显示的 ToolStrip 对象模型的关系图。](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 您可以访问中的所有项<xref:System.Windows.Forms.ToolStrip>通过<xref:System.Windows.Forms.ToolStrip.Items%2A>集合。 您可以访问中的所有项<xref:System.Windows.Forms.ToolStripDropDownItem>通过<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>集合。 在派生类中<xref:System.Windows.Forms.ToolStrip>，还可以使用<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>属性访问当前显示这些项。 这些是当前未在溢出菜单中的项。  
  
 以下各项专门用于两个无缝<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>在所有方向。 这些信息可默认情况下在设计时<xref:System.Windows.Forms.ToolStrip>控件：  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> 为取代的顶级容器<xref:System.Windows.Forms.MainMenu>。 它还提供密钥的处理和多文档界面 (MDI) 功能。 就功能而言，<xref:System.Windows.Forms.ToolStripDropDownItem>并<xref:System.Windows.Forms.ToolStripMenuItem>连同工作<xref:System.Windows.Forms.MenuStrip>，尽管它们派生自<xref:System.Windows.Forms.ToolStripItem>。  
  
 以下各项专门用于两个无缝<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>在所有方向。 这些信息可默认情况下在设计时<xref:System.Windows.Forms.MenuStrip>控件：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> 替换<xref:System.Windows.Forms.StatusBar>控件。 特殊功能<xref:System.Windows.Forms.StatusStrip>包括自定义表布局、 支持的窗体的大小调整和移动手柄，并`Spring`属性，它允许<xref:System.Windows.Forms.ToolStripStatusLabel>以自动填充可用空间。  
  
 以下各项专门用于两个无缝<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>在所有方向。 这些信息可默认情况下在设计时<xref:System.Windows.Forms.StatusStrip>控件：  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> 替代 <xref:System.Windows.Forms.ContextMenu>。 你可以将关联<xref:System.Windows.Forms.ContextMenuStrip>使用任何控制和鼠标右键单击将自动显示上下文菜单 （或快捷菜单）。 可以显示<xref:System.Windows.Forms.ContextMenuStrip>以编程方式使用<xref:System.Windows.Forms.ToolStripDropDown.Show%2A>方法。 <xref:System.Windows.Forms.ContextMenuStrip> 支持可取消<xref:System.Windows.Forms.ToolStripDropDown.Opening>和<xref:System.Windows.Forms.ToolStripDropDown.Closing>事件以处理动态填充并多次单击方案。 <xref:System.Windows.Forms.ContextMenuStrip> 支持图像、 菜单项复选状态、 文本、 访问密钥、 快捷方式和级联菜单。  
  
 以下各项专门用于两个无缝<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>在所有方向。 这些信息可默认情况下在设计时<xref:System.Windows.Forms.ContextMenuStrip>控件：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip 泛型功能  
 以下主题介绍的功能和行为是通用的<xref:System.Windows.Forms.ToolStrip>和派生的控件。  
  
#### <a name="painting"></a>绘制  
 可以执行自定义绘制<xref:System.Windows.Forms.ToolStrip>几种方法中的控件。 与其他 Windows 窗体控件一样，<xref:System.Windows.Forms.ToolStrip>并<xref:System.Windows.Forms.ToolStripItem>两者都具有可重写`OnPaint`方法和`Paint`事件。 因为与常规的绘制坐标系统是相对于控件; 客户端区域也就是说，该控件的左上角为 0，0。 `Paint`事件和`OnPaint`方法<xref:System.Windows.Forms.ToolStripItem>的行为类似于其他控件绘制事件。  
  
 <xref:System.Windows.Forms.ToolStrip>控件还提供更细致的访问的项和容器可以通过呈现<xref:System.Windows.Forms.ToolStripRenderer>类，该类包含对于绘制背景、 项背景色、 项图像、 项箭头、 项文本的可重写方法，和边框<xref:System.Windows.Forms.ToolStrip>. 这些方法的事件自变量公开多个属性，如矩形、 颜色和文本格式，可以根据需要调整。  
  
 若要调整的几个方面如何绘制项，通常可以重写<xref:System.Windows.Forms.ToolStripRenderer>。  
  
 如果你正在编写新项，并想要控制绘制的所有方面，重写`OnPaint`方法。 从内部`OnPaint`，可以使用从方法<xref:System.Windows.Forms.ToolStripRenderer>。  
  
 默认情况下<xref:System.Windows.Forms.ToolStrip>进行双缓冲，充分利用<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>设置。  
  
#### <a name="parenting"></a>设置父级  
 容器所属权和设置父级的概念是在更复杂<xref:System.Windows.Forms.ToolStrip>比在其他 Windows 窗体容器控件中的控件。 这是支持动态方案，例如溢出，跨多个共享下拉项所需<xref:System.Windows.Forms.ToolStrip>项，并支持一代<xref:System.Windows.Forms.ContextMenuStrip>从控件。  
  
 以下列表介绍子女教养与相关的成员，并说明其用途。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> 访问源的下拉列表项的项。 它类似于<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>，而不是返回一个控件，它将返回，但<xref:System.Windows.Forms.ToolStripItem>。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> 确定哪个控件是源的<xref:System.Windows.Forms.ContextMenuStrip>当多个控件都共享相同<xref:System.Windows.Forms.ContextMenuStrip>。  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> 是对只读访问器<xref:System.Windows.Forms.ToolStripItem.Parent%2A>属性。 父级不同于所有者，父级表示返回的当前<xref:System.Windows.Forms.ToolStrip>中的项显示，则其可能处于溢出区域。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> 返回<xref:System.Windows.Forms.ToolStrip>其项集合包含当前<xref:System.Windows.Forms.ToolStripItem>。 这是最佳的方式来引用<xref:System.Windows.Forms.ToolStrip.ImageList%2A>或其他属性在顶级<xref:System.Windows.Forms.ToolStrip>而无需编写特殊代码，以处理溢出。  
  
#### <a name="behavior-of-inherited-controls"></a>继承的控件的行为  
 以下控件被锁定在继承中使用它们时：  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 包括在面板<xref:System.Windows.Forms.ToolStripContainer>和也各个<xref:System.Windows.Forms.ToolStripPanel>控件。  
  
 例如，使用前面的列表中的一个或多个控件中创建新的 Windows 窗体应用程序。 设置到一个或多个控件的访问修饰符`public`或`protected`，然后生成项目。 添加从第一个窗体继承一个窗体，然后选择继承的控件。 该控件将出现锁定状态，行为就像其访问修饰符是`private`。  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer 支持的继承  
 <xref:System.Windows.Forms.ToolStripContainer>控件支持有限的继承的方案，类似于下面的示例：  
  
1.  创建新的 Windows 窗体应用程序。  
  
2.  在窗体上添加一个 <xref:System.Windows.Forms.ToolStripContainer> 控件。  
  
3.  设置的访问修饰符<xref:System.Windows.Forms.ToolStripContainer>到`public`或`protected`。  
  
4.  添加的任意组合<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，并<xref:System.Windows.Forms.ContextMenuStrip>控件添加到<xref:System.Windows.Forms.ToolStripPanel>的区域<xref:System.Windows.Forms.ToolStripContainer>。  
  
5.  生成项目。  
  
6.  添加从第一个窗体继承一个窗体。  
  
7.  选择继承<xref:System.Windows.Forms.ToolStripContainer>窗体上。  
  
#### <a name="inherited-behavior-of-child-controls"></a>子控件的继承的行为  
 完成前面的步骤后，将发生以下继承的行为：  
  
-   在设计器中，该控件显示继承的图标。  
  
-   <xref:System.Windows.Forms.ToolStripPanel>控件被锁定，不能选择或重新排列其内容。  
  
-   您可以将控件添加到<xref:System.Windows.Forms.ToolStripContentPanel>、 移动控件，并使它们的子控件<xref:System.Windows.Forms.ToolStripContentPanel>。  
  
-   构建窗体后保留所做的更改。  
  
    > [!NOTE]
    >  从所有删除访问修饰符<xref:System.Windows.Forms.ToolStripPanel>一部分的控件<xref:System.Windows.Forms.ToolStripContainer>。 访问修饰符的<xref:System.Windows.Forms.ToolStripContainer>控制整个控件。  
  
#### <a name="partial-trust"></a>部分信任  
 限制`ToolStrip`部分信任环境下的 s 旨在防止无意中输入的可能被未经授权的人员或服务使用的个人信息。 保护性措施是，如下所示：  
  
-   `ToolStripDropDown` 控件需要<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>若要显示在项<xref:System.Windows.Forms.ToolStripControlHost>。 这包括适用于这两个内部控件<xref:System.Windows.Forms.ToolStripTextBox>， <xref:System.Windows.Forms.ToolStripComboBox>，和<xref:System.Windows.Forms.ToolStripProgressBar>作为以及给用户创建控件。 如果不满足此要求，则不显示这些项。 不引发异常。  
  
-   设置<xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A>属性设置为`false`不允许，可取消<xref:System.Windows.Forms.ToolStripDropDown.Closing>事件参数将被忽略。 这样就不可能以输入多个击键，而不关闭下拉列表项。 如果不满足此要求，则不显示此类项。 不引发异常。  
  
-   如果它们不是出现在部分信任上下文中，将不会引发多个键击处理事件<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>。  
  
-   访问键不是处理时<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>未被授予。  
  
#### <a name="usage"></a>用法  
 以下使用情况模式会重的负担<xref:System.Windows.Forms.ToolStrip>布局、 键盘交互和最终用户行为：  
  
-   已加入 <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip>可以中重新定位<xref:System.Windows.Forms.ToolStripPanel>并跨<xref:System.Windows.Forms.ToolStripPanel>s。 `Dock`属性将被忽略，并且如果<xref:System.Windows.Forms.ToolStrip.Stretch%2A>属性是`false`，则大小<xref:System.Windows.Forms.ToolStrip>随着项添加到<xref:System.Windows.Forms.ToolStripPanel>。 通常情况下，<xref:System.Windows.Forms.ToolStrip>不参与 tab 键顺序。  
  
-   停靠  
  
     <xref:System.Windows.Forms.ToolStrip>的固定位置中的容器一侧放置其大小扩展通过向其停靠的整条边。 通常情况下，<xref:System.Windows.Forms.ToolStrip>不参与 tab 键顺序。  
  
-   绝对定位  
  
     <xref:System.Windows.Forms.ToolStrip>相当于其他控件，可由放置<xref:System.Windows.Forms.Control.Location%2A>属性，具有固定的大小，通常会参与 tab 键顺序。  
  
#### <a name="keyboard-interaction"></a>键盘交互  
  
##### <a name="access-keys"></a>访问密钥  
 访问密钥组合使用或紧随 ALT 键，是一种方式激活使用键盘的控件。 <xref:System.Windows.Forms.ToolStrip> 支持这两个显式和隐式访问密钥。 显式定义使用 and 符 (&) 字符前面的字母。 隐式定义使用一种算法，尝试查找匹配项中的字符顺序基于给定`Text`属性。  
  
##### <a name="shortcut-keys"></a>快捷键  
 使用的键盘快捷方式<xref:System.Windows.Forms.MenuStrip>结合使用<xref:System.Windows.Forms.Keys>枚举 （这不是特定于顺序的） 来定义的快捷键。 此外可以使用<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>属性来显示具有纯文本的快捷方式键，例如，显示"Del"而不"删除"。  
  
##### <a name="navigation"></a>导航  
 ALT 键时激活<xref:System.Windows.Forms.MenuStrip>指向的<xref:System.Windows.Forms.Form.MainMenuStrip%2A>。 在这里，CTRL + TAB 导航之间<xref:System.Windows.Forms.ToolStrip>控件的`ToolStripPanel`s。 中的项之间的 TAB 键和数字键盘上的箭头键导航<xref:System.Windows.Forms.ToolStrip>。 特殊算法处理中的溢出区域的导航。 空格键选择<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，或<xref:System.Windows.Forms.ToolStripSplitButton>。  
  
##### <a name="focus-and-validation"></a>焦点和验证  
 按 ALT 键激活时<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ToolStrip>通常既不需要也不删除从当前具有焦点的控件的焦点。 如果没有中承载的控件<xref:System.Windows.Forms.MenuStrip>或下拉列表的<xref:System.Windows.Forms.MenuStrip>，该控件在用户按 TAB 键时获得焦点。 一般情况下， <xref:System.Windows.Forms.Control.GotFocus>， <xref:System.Windows.Forms.Control.LostFocus>， <xref:System.Windows.Forms.Control.Enter>，和<xref:System.Windows.Forms.Control.Leave>的事件<xref:System.Windows.Forms.MenuStrip>可能无法通过键盘激活时引发。 在这种情况下，使用<xref:System.Windows.Forms.MenuStrip.MenuActivate>和<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>事件相反。  
  
 默认情况下<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>是`false`。 调用<xref:System.Windows.Forms.ContainerControl.Validate%2A>显式在窗体来执行验证。  
  
#### <a name="layout"></a>布局  
 您可以控制<xref:System.Windows.Forms.ToolStrip>通过选择其中一个的成员布局<xref:System.Windows.Forms.ToolStripLayoutStyle>与<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>属性。  
  
##### <a name="stack-layouts"></a>堆栈布局  
 堆栈是并排排列项相互的两端<xref:System.Windows.Forms.ToolStrip>。 以下列表介绍了堆栈布局。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> 默认值。 此设置会导致<xref:System.Windows.Forms.ToolStrip>若要更改其自动根据所使用的布局<xref:System.Windows.Forms.ToolStrip.Orientation%2A>属性来处理拖动和停靠的方案。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> 呈现<xref:System.Windows.Forms.ToolStrip>项旁边相互垂直。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> 呈现<xref:System.Windows.Forms.ToolStrip>水平并排的项。  
  
##### <a name="other-features-of-stack-layouts"></a>其他功能的堆栈布局  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 决定结束的<xref:System.Windows.Forms.ToolStrip>与之对齐项。  
  
 当项不可纳入<xref:System.Windows.Forms.ToolStrip>，会自动显示溢出按钮。 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>属性设置用于确定某个项中是否显示溢出区域根据需要始终或从不。  
  
 在中<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件中，可以检查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>属性来确定某项放在主<xref:System.Windows.Forms.ToolStrip>，溢出<xref:System.Windows.Forms.ToolStrip>，或如果当前根本未显示。 为什么不显示该项的通常原因是该项未不放置在主<xref:System.Windows.Forms.ToolStrip>并将其<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>属性设置为<xref:System.Windows.Forms.ToolStripItemOverflow.Never>。  
  
 请<xref:System.Windows.Forms.ToolStrip>将其放入可移动<xref:System.Windows.Forms.ToolStripPanel>并设置其<xref:System.Windows.Forms.ToolStrip.GripStyle%2A>到<xref:System.Windows.Forms.ToolStripGripStyle.Visible>。  
  
##### <a name="other-layout-options"></a>其他布局选项  
 其他布局选项<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>和<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>。  
  
##### <a name="flow-layout"></a>流布局  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> 布局是默认值<xref:System.Windows.Forms.ContextMenuStrip>， <xref:System.Windows.Forms.ToolStripDropDownMenu>，和<xref:System.Windows.Forms.ToolStripOverflow>。 它相当于<xref:System.Windows.Forms.FlowLayoutPanel>。 功能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>布局如下所示：  
  
-   所有的功能<xref:System.Windows.Forms.FlowLayoutPanel>公开的<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>属性。 必须强制转换<xref:System.Windows.Forms.LayoutSettings>类来<xref:System.Windows.Forms.FlowLayoutSettings>类。  
  
-   可以使用<xref:System.Windows.Forms.ToolStripItem.Dock%2A>和<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>代码以对齐在行中的项中的属性。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 属性被忽略。  
  
-   在中<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件中，可以检查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>属性来确定某项放在主<xref:System.Windows.Forms.ToolStrip>还是无法容纳。  
  
-   不呈现手柄，并因此<xref:System.Windows.Forms.ToolStrip>中<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>中的布局样式<xref:System.Windows.Forms.ToolStripPanel>不能移动。  
  
-   <xref:System.Windows.Forms.ToolStrip>不呈现溢出按钮时，和<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>将被忽略。  
  
##### <a name="table-layout"></a>表布局  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> 布局是的默认值为<xref:System.Windows.Forms.StatusStrip>。 它相当于<xref:System.Windows.Forms.TableLayoutPanel>。 功能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>布局如下所示：  
  
-   所有的功能<xref:System.Windows.Forms.TableLayoutPanel>公开的<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>属性。 必须强制转换<xref:System.Windows.Forms.LayoutSettings>类来<xref:System.Windows.Forms.TableLayoutSettings>类。  
  
-   可以使用<xref:System.Windows.Forms.ToolStripItem.Dock%2A>和<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>对齐表格单元格内的项的代码中的属性。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 属性被忽略。  
  
-   在中<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件中，可以检查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>属性来确定某项放在主<xref:System.Windows.Forms.ToolStrip>还是无法容纳。  
  
-   不呈现手柄，并因此<xref:System.Windows.Forms.ToolStrip>中<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>中的布局样式<xref:System.Windows.Forms.ToolStripPanel>不能移动。  
  
-   <xref:System.Windows.Forms.ToolStrip>不呈现溢出按钮时，和<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>将被忽略。  
  
## <a name="toolstripitem"></a>ToolStripItem  
 下面的主题介绍<xref:System.Windows.Forms.ToolStripItem>和从其派生的控件。  
  
 <xref:System.Windows.Forms.ToolStripItem> 是进入的所有项的抽象基类<xref:System.Windows.Forms.ToolStrip>。 下面的对象模型演示<xref:System.Windows.Forms.ToolStripItem>继承层次结构。  
  
 ![显示 ToolStripItem 对象模型的关系图。](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> 直接从继承的类<xref:System.Windows.Forms.ToolStripItem>，或间接从继承<xref:System.Windows.Forms.ToolStripItem>通过<xref:System.Windows.Forms.ToolStripControlHost>或<xref:System.Windows.Forms.ToolStripDropDownItem>。  
  
 <xref:System.Windows.Forms.ToolStripItem> 控件必须包含在<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.StatusStrip>，或<xref:System.Windows.Forms.ContextMenuStrip>和不能直接添加到窗体。 各种容器类旨在包含相应子集<xref:System.Windows.Forms.ToolStripItem>控件。  
  
 下表列出了股票<xref:System.Windows.Forms.ToolStripItem>控件和他们查找最佳的容器。 尽管任何<xref:System.Windows.Forms.ToolStrip>项可以承载于任何<xref:System.Windows.Forms.ToolStrip>-派生的容器，这些项目旨在看起来效果最佳以下容器中：  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> 不会显示在设计器工具箱中。  
  
|包含的项目|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|是|否|否|否|是|  
|<xref:System.Windows.Forms.ToolStripComboBox>|是|是|是|No|是|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripLabel>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripSeparator>|是|是|是|No|是|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripTextBox>|是|是|是|No|是|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|No|是|是|否|否|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|否|否|否|是|No|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|是|否|否|是|No|  
|<xref:System.Windows.Forms.ToolStripControlHost>|是|是|No|是|是|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> 按钮项<xref:System.Windows.Forms.ToolStrip>。 显示具有不同的边框样式，并可用来表示和激活的操作状态。 此外可以定义它默认情况下具有焦点。  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel>提供了标签功能<xref:System.Windows.Forms.ToolStrip>控件。 <xref:System.Windows.Forms.ToolStripLabel>类似于<xref:System.Windows.Forms.ToolStripButton>，默认情况下不获得焦点并不会呈现为推送或突出显示。  
  
 <xref:System.Windows.Forms.ToolStripLabel> 作为托管项支持访问密钥。  
  
 使用<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>，并<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>上的属性<xref:System.Windows.Forms.ToolStripLabel>若要支持中的链接控制<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> 是的版本<xref:System.Windows.Forms.ToolStripLabel>专门设计用于在<xref:System.Windows.Forms.StatusStrip>。 特殊功能包括<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>， <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>，和<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>。  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator>将垂直或水平行添加到工具栏或菜单上，根据方向。 它提供了分组或项，如菜单上的那些之间的区别。  
  
 您可以添加<xref:System.Windows.Forms.ToolStripSeparator>在设计时通过从下拉列表中选择它。 但是，还会自动可以创建<xref:System.Windows.Forms.ToolStripSeparator>键入一个连字符 （-） 在设计器的模板节点中或在<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法。  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> 是的抽象基类<xref:System.Windows.Forms.ToolStripComboBox>， <xref:System.Windows.Forms.ToolStripTextBox>，和<xref:System.Windows.Forms.ToolStripProgressBar>。 <xref:System.Windows.Forms.ToolStripControlHost> 可以托管其他控件，包括自定义控件，通过两种方式：  
  
-   构造<xref:System.Windows.Forms.ToolStripControlHost>派生的类<xref:System.Windows.Forms.Control>。 若要完全访问托管的控件和属性，必须转换<xref:System.Windows.Forms.ToolStripControlHost.Control%2A>属性设置为的实际类它表示。  
  
-   扩展<xref:System.Windows.Forms.ToolStripControlHost>，并在继承的类默认构造函数中调用基类构造函数传递派生的类<xref:System.Windows.Forms.Control>。 此选项可以用于在轻松访问常见控件方法和属性包装<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> 是<xref:System.Windows.Forms.ComboBox>适合用来托管在<xref:System.Windows.Forms.ToolStrip>。 在公开的托管的控件的属性和事件子集<xref:System.Windows.Forms.ToolStripComboBox>级别，但基础<xref:System.Windows.Forms.ComboBox>控件是完全可通过访问<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>属性。  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> 是<xref:System.Windows.Forms.TextBox>适合用来托管在<xref:System.Windows.Forms.ToolStrip>。 在公开的托管的控件的属性和事件子集<xref:System.Windows.Forms.ToolStripTextBox>级别，但基础<xref:System.Windows.Forms.TextBox>控件是完全可通过访问<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>属性。  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> 是<xref:System.Windows.Forms.ProgressBar>适合用来托管在<xref:System.Windows.Forms.ToolStrip>。 在公开的托管的控件的属性和事件子集<xref:System.Windows.Forms.ToolStripProgressBar>级别，但基础<xref:System.Windows.Forms.ProgressBar>控件是完全可通过访问<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>属性。  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> 是的抽象基类<xref:System.Windows.Forms.ToolStripMenuItem>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>，这可以托管项直接或主机下拉容器中的其他项。 执行此操作通过设置<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>属性设置为<xref:System.Windows.Forms.ToolStripDropDown>并设置<xref:System.Windows.Forms.ToolStrip.Items%2A>属性的<xref:System.Windows.Forms.ToolStripDropDown>。 访问这些下拉列表项直接通过<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>属性。  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> 是<xref:System.Windows.Forms.ToolStripDropDownItem>这是使用<xref:System.Windows.Forms.ToolStripDropDownMenu>和<xref:System.Windows.Forms.ContextMenuStrip>来处理特殊的突出显示、 布局和列排列的菜单。  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> 看起来像<xref:System.Windows.Forms.ToolStripButton>，但它显示了下拉区域，当用户单击它。 隐藏或显示的下拉箭头，通过设置<xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>属性。 <xref:System.Windows.Forms.ToolStripDropDownButton> 主机<xref:System.Windows.Forms.ToolStripOverflowButton>显示溢出项<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> 按钮和下拉按钮的功能相结合。  
  
 使用<xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>属性来同步<xref:System.Windows.Forms.Control.Click>按钮上显示的项与所选的下拉列表项的事件。  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem 泛型功能  
 <xref:System.Windows.Forms.ToolStripItem> 提供了以下泛型功能和到继承控件的选项：  
  
-   核心事件  
  
-   图像处理  
  
-   对齐方式  
  
-   文本和图像的关系  
  
-   显示样式  
  
#### <a name="core-events"></a>核心事件  
 <xref:System.Windows.Forms.ToolStripItem> 控件接收其自己的单击、 鼠标和绘制事件，并且可以执行某些键盘还预处理。  
  
#### <a name="image-handling"></a>图像处理  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>，和<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>属性与图像处理的各个方面。 使用中的映像<xref:System.Windows.Forms.ToolStrip>控件通过设置这些属性直接或通过设置运行--仅限时间<xref:System.Windows.Forms.ToolStrip.ImageList%2A>属性。  
  
 图像缩放由在这种属性的交互<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>，按如下所示：  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> 图像的组合所确定的最终图像的小数位数<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>设置和容器的<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>设置。  
  
    -   如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>是`true`（默认值） 和<xref:System.Windows.Forms.ToolStripItemImageScaling>是<xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>，会发生任何图像缩放，和<xref:System.Windows.Forms.ToolStrip>大小是最大项或规定的最小大小。  
  
    -   如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>是`false`并<xref:System.Windows.Forms.ToolStripItemImageScaling>是<xref:System.Windows.Forms.ToolStripItemImageScaling.None>，既不映像，也不<xref:System.Windows.Forms.ToolStrip>缩放会发生。  
  
#### <a name="alignment"></a>对齐方式  
 值<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>属性确定的末尾<xref:System.Windows.Forms.ToolStrip>在出现的项。 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>属性时才起作用的布局样式<xref:System.Windows.Forms.ToolStrip>设置为堆栈溢出值之一。  
  
 项放置在<xref:System.Windows.Forms.ToolStrip>中项的项集合中的显示的顺序。 若要以编程方式更改项进行布局，请使用<xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>方法将集合中的项。 此方法会将项移动，但不能复制它。  
  
#### <a name="text-and-image-relationship"></a>文本和图像关系  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>属性定义相对于文本图像的相对位置上<xref:System.Windows.Forms.ToolStripItem>。 缺少图像、 文本或这两项将被视为特殊情况下，以便<xref:System.Windows.Forms.ToolStripItem>不会显示缺少的元素或元素的空白处。  
  
#### <a name="display-style"></a>显示样式  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 可以同时显示你只想设置项的文本和图像属性的值。 这通常用于不同的上下文中显示的相同项时更改仅显示样式。  
  
## <a name="accessory-classes"></a>附件类  
 类提供各种其他功能包括：  
  
-   <xref:System.Windows.Forms.ToolStripManager> 支持<xref:System.Windows.Forms.ToolStrip>-相关的任务对于整个应用程序，例如合并、 设置和呈现器的选项。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> 允许您将应用特定样式或主题应用于<xref:System.Windows.Forms.ToolStrip>轻松。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 创建钢笔和画笔基于可更换部件颜色表 (<xref:System.Windows.Forms.ProfessionalColorTable>)。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> 将系统颜色和平面视觉样式为<xref:System.Windows.Forms.ToolStrip>应用程序。  
  
-   <xref:System.Windows.Forms.ToolStripContainer> 类似于<xref:System.Windows.Forms.SplitContainer>。 它使用四个停靠的侧面板 (的实例<xref:System.Windows.Forms.ToolStripPanel>) 和一个中间面板 (实例<xref:System.Windows.Forms.ToolStripContentPanel>) 若要创建典型的排列方式。 不能删除侧面板，但可以隐藏它们。 不能删除或隐藏中间面板。 一个或多个可以排列<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，或<xref:System.Windows.Forms.StatusStrip>侧面板，，和中的控件可以使用其他控件的中间面板。 <xref:System.Windows.Forms.ToolStripContentPanel>还提供了一种方法获取呈现器支持到实现一致的外观窗体的正文。 <xref:System.Windows.Forms.ToolStripContainer> 不支持多文档界面 (MDI)。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 用于移动和排列提供空间<xref:System.Windows.Forms.ToolStrip>控件。 如果这样选择，可以使用只有一个面板和<xref:System.Windows.Forms.ToolStripPanel>适用于 MDI 方案。  
  
## <a name="see-also"></a>请参阅
- [ToolStrip 控件概述](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 技术摘要](toolstrip-technology-summary.md)
- [ToolStrip 控件](toolstrip-control-windows-forms.md)
- [MenuStrip 控件](menustrip-control-windows-forms.md)
- [StatusStrip 控件](statusstrip-control.md)
- [ContextMenuStrip 控件](contextmenustrip-control.md)
- [BindingNavigator 控件](bindingnavigator-control-windows-forms.md)
