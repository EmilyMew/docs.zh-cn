---
title: Windows 窗体中的用户输入验证
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: c8a40706df4274728b438cff2539173a0e94b767
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076674"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows 窗体中的用户输入验证
当用户输入到你的应用程序数据时，你可以验证数据有效，然后再在应用程序将使用它。 可能需要某些文本字段不为零长度、 字段将格式化为电话号码或其他类型的格式正确的数据，或字符串不包含任何不安全字符无法用于危及安全的数据库。 Windows 窗体提供了几种方法，以验证你的应用程序中的输入。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>使用 MaskedTextBox 控件进行验证  
 如果你需要要求用户输入数据中的定义完善的格式，如电话号码或部分数字，你可以完成此操作速度快、 最少的代码使用<xref:System.Windows.Forms.MaskedTextBox>控件。 一个*掩码*是指定可以在任何给定位置在文本框中输入的字符的掩码语言的字符组成的字符串。 控件向用户显示一组提示。 如果用户键入的不正确的条目，例如，在用户键入字母数字时所需，该控件将自动拒绝输入。  
  
 使用的掩码语言<xref:System.Windows.Forms.MaskedTextBox>非常灵活。 它允许您指定所需的字符、 可选的字符、 原义字符，如连字符和括号，货币字符和日期分隔符。 该控件也适用于良好时绑定到数据源。 <xref:System.Windows.Forms.Binding.Format>上的数据绑定事件可用于重新设置格式传入的数据以符合掩码和<xref:System.Windows.Forms.Binding.Parse>事件可用于重新格式化传出的数据以遵守与数据字段的规范。  
  
 有关详细信息，请参阅[MaskedTextBox 控件](./controls/maskedtextbox-control-windows-forms.md)。  
  
## <a name="event-driven-validation"></a>事件驱动的验证  
 如果您想要完整的编程控制验证，或需要执行复杂的验证检查，则应使用大多数 Windows 窗体控件中内置的验证事件。 接受自由的用户输入的每个控件具有<xref:System.Windows.Forms.Control.Validating>每当该控件所需数据验证时将发生的事件。 在<xref:System.Windows.Forms.Control.Validating>事件处理方法，可以验证用户输入以下几种方式。 例如，如果您有必须包含邮政编码的文本框中，您可以按以下方式来执行验证：  
  
-   如果邮政编码必须属于特定组的邮政编码，您可以对要验证用户输入的数据的输入执行字符串比较。 例如，如果邮政编码必须为 {10001、 10002，10003} 集中，然后可以使用字符串比较来验证数据。  
  
-   如果邮政编码必须为特定窗体中您可以使用正则表达式验证用户输入的数据。 例如，若要验证的表单`#####`或`#####-####`，可以使用正则表达式`^(\d{5})(-\d{4})?$`。 若要验证的表单`A#A #A#`，可以使用正则表达式`[A-Z]\d[A-Z] \d[A-Z]\d`。 有关正则表达式的详细信息，请参阅[.NET Framework 正则表达式](../../standard/base-types/regular-expressions.md)并[正则表达式示例](../../standard/base-types/regular-expression-examples.md)。  
  
-   如果邮政编码必须是有效的美国邮政编码，则可以调用邮政编码 Web 服务，以便验证用户输入的数据。  
  
 <xref:System.Windows.Forms.Control.Validating>提供事件类型的对象<xref:System.ComponentModel.CancelEventArgs>。 如果您确定控件的数据无效，则可以取消<xref:System.Windows.Forms.Control.Validating>通过设置此对象的事件<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性设置为`true`。 如果未设置<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性，Windows 窗体将假定该验证已成功为该控件，并引发<xref:System.Windows.Forms.Control.Validated>事件。  
  
 有关验证电子邮件地址中的代码示例<xref:System.Windows.Controls.TextBox>，请参阅<xref:System.Windows.Forms.Control.Validating>。  
  
### <a name="data-binding-and-event-driven-validation"></a>数据绑定和事件驱动的验证  
 将控件绑定到数据源，例如数据库表时，验证会非常有用。 通过使用验证，你可以确保控件的数据满足所需的数据源的格式和它不包含任何特殊字符如引号和备份正斜杠可能不安全。  
  
 如果使用数据绑定，在控件中的数据与同步数据源执行期间<xref:System.Windows.Forms.Control.Validating>事件。 如果您取消<xref:System.Windows.Forms.Control.Validating>事件，不会与数据源同步数据。  
  
> [!IMPORTANT]
>  如果您有后会发生的自定义验证<xref:System.Windows.Forms.Control.Validating>事件，它将不会影响数据绑定。 例如，如果您的代码<xref:System.Windows.Forms.Control.Validated>尝试取消数据绑定的事件，仍会发生数据绑定。 在此情况下，若要执行中的验证<xref:System.Windows.Forms.Control.Validated>事件，更改控件的**数据源更新模式**属性 (**在 (Databindings) 下**\\ **（高级）**) 从**OnValidation**到**从不**，并添加*控制*`.DataBindings["`*\<YOURFIELD >* `"].WriteValue()`到您的验证代码。  
  
### <a name="implicit-and-explicit-validation"></a>隐式和显式验证  
 因此何时控件的数据验证？ 这是取决于您，开发人员。 可以使用隐式或显式验证，具体取决于应用程序的需求。  
  
#### <a name="implicit-validation"></a>隐式验证  
 当用户输入其会隐式验证方法验证数据。 为通常只要用户将输入的焦点离开控件并移动到下一步中通过读取密钥，因为它们被按下，控件或多个输入数据后，可以验证数据。 当您希望他们正在为用户有关的数据的即时反馈，此方法非常有用。  
  
 如果你想要使用的控件的隐式验证，则必须设置该控件的<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>属性设置为`true`。 如果您取消<xref:System.Windows.Forms.Control.Validating>事件，该控件的行为将由你分配给的值<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>。 如果您分配<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>，取消该事件将导致<xref:System.Windows.Forms.Control.Validated>事件不发生。 输入的焦点将保留在当前控件，直到用户将数据更改为有效的输入。 如果您分配<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>，则<xref:System.Windows.Forms.Control.Validated>时取消该事件，但焦点仍将更改到下一个控件，不会出现事件。  
  
 将分配<xref:System.Windows.Forms.AutoValidate.Disable>到<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>属性会完全阻止隐式验证。 若要验证您的控件，您将需要使用显式验证。  
  
#### <a name="explicit-validation"></a>显式验证  
 显式验证方法验证一次数据。 可以验证响应用户操作，例如单击保存按钮或下一个链接中的数据。 当用户执行任何操作发生时，可以通过以下方式之一来触发显式验证：  
  
-   调用<xref:System.Windows.Forms.ContainerControl.Validate%2A>来验证失去焦点的最后一个控件。  
  
-   调用<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>来验证窗体或容器控件中的所有子控件。  
  
-   调用自定义的方法来手动验证控件中的数据。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>默认隐式验证行为的 Windows 窗体控件  
 不同的 Windows 窗体控件具有不同的默认值为其<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>属性。 下表显示了最常用的控件和各自的默认值。  
  
|控件|默认验证行为|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio 中未公开的属性|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio 中未公开的属性|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>关闭该窗体和重写验证  
 当控件保持焦点，因为它包含的数据无效时，就无法关闭父窗体中的常用方法之一：  
  
-   通过单击**关闭**按钮。  
  
-   通过选择**关闭**中**系统**菜单。  
  
-   通过调用<xref:System.Windows.Forms.Form.Close%2A>方法以编程方式。  
  
 但是，在某些情况下，你可能想要让用户关闭该窗体而不考虑在控件中的值是否有效。 您可以重写验证并关闭仍通过创建窗体的一个处理程序中包含无效数据的窗体<xref:System.Windows.Forms.Form.Closing>事件。 在事件中，设置<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>属性设置为`false`。 这会强制关闭该窗体。 有关详细信息及示例，请参阅<xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>。  
  
> [!NOTE]
>  如果强制以这种方式关闭该窗体时，会丢失尚未保存的窗体的控件中的任何数据。 此外，有模式窗体关闭时不会验证的控件的内容。 您仍可以使用控件验证锁定焦点设置到一个控件，但不是需要关心如何与关闭该窗体关联的行为。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox 控件](./controls/maskedtextbox-control-windows-forms.md)
- [正则表达式示例](../../standard/base-types/regular-expression-examples.md)
