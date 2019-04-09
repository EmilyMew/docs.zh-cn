---
title: 演练：使用 XAML 创建按钮
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: c092ad49f40257467245a07a6e4b9849822e1835
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076557"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>演练：使用 XAML 创建按钮
本演练的目的是了解如何创建 Windows Presentation Foundation (WPF) 应用程序中使用的动画的按钮。 本演练使用样式和模板来创建自定义的按钮资源允许重用代码和从按钮声明按钮逻辑的分离。 本演练完全在编写[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
> [!IMPORTANT]
>  本演练将指导您完成创建应用程序，通过键入或复制并粘贴步骤[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]到 Microsoft Visual Studio。 如果你想要了解如何使用设计工具 (Microsoft Expression Blend) 来创建相同的应用程序，请参阅[创建一个按钮通过使用 Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)。  
  
 下图显示了已完成的按钮。  
  
 ![通过使用 XAML 创建的自定义按钮](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>创建基本按钮  
 让我们首先创建一个新项目并将几个按钮添加到窗口。  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>若要创建新的 WPF 项目并将按钮添加到窗口  
  
1.  启动 Visual Studio。  
  
2.  **创建新的 WPF 项目：** 在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。 查找**Windows 应用程序 (WPF)** 模板，并命名项目"AnimatedButton"。 这将创建应用程序的主干。  
  
3.  **添加基本的默认按钮：** 在本演练中所需的所有文件均由模板都提供。 通过双击它在解决方案资源管理器中打开 Window1.xaml 文件。 默认情况下，没有<xref:System.Windows.Controls.Grid>在 Window1.xaml 中的元素。 删除<xref:System.Windows.Controls.Grid>元素，并添加到了几个按钮[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]通过键入或复制并粘贴到 Window1.xaml 以下突出显示的代码页：  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>  
    </Window>  
    ```  
  
     按 F5 运行该应用程序;您将看到类似于下图的按钮的组。  
  
     ![三个基本按钮](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     现在，已创建的基本按钮，您已完成 Window1.xaml 文件中的工作。 本演练的其余部分重点介绍 app.xaml 文件中，定义样式和模板的按钮。  
  
## <a name="set-basic-properties"></a>设置基本属性  
 接下来，让我们来设置这些按钮来控制按钮外观和布局的某些属性。 而不是单独在按钮上设置属性，将使用的资源来定义整个应用程序的按钮属性。 应用程序资源是从概念上讲类似于外部[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]网页; 但是，资源将比强大得多[!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)]，正如您将看到本演练结束。 若要了解有关资源的详细信息，请参阅[XAML 资源](../advanced/xaml-resources.md)。  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>若要使用样式按钮上设置基本属性  
  
1.  **定义 Application.Resources 块：** 打开 app.xaml 并添加以下突出显示的标记，如果尚不存在：  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     您在其中定义资源取决于资源范围。 定义中的资源`Application.Resources`在 app.xaml 文件，要使用从任意位置的应用程序中的资源。 若要了解有关定义你的资源范围的详细信息，请参阅[XAML 资源](../advanced/xaml-resources.md)。  
  
2.  **创建一个样式，并定义与它的基本属性值：** 添加以下标记到`Application.Resources`块。 此标记创建<xref:System.Windows.Style>应用于的应用程序设置中的所有按钮<xref:System.Windows.FrameworkElement.Width%2A>的按钮为 90 和<xref:System.Windows.FrameworkElement.Margin%2A>到 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A>属性指定该样式应用于类型的所有对象<xref:System.Windows.Controls.Button>。 每个<xref:System.Windows.Setter>设置为不同的属性值<xref:System.Windows.Style>。 因此，此时应用程序中的每个按钮具有宽度为 90、 边距为 10。  如果按 F5 运行该应用程序时，你会看到以下窗口。  
  
     ![具有宽度为 90、 边距为 10 的按钮](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     没有你可以执行更多使用样式，包括各种的方式来优化对象的目标、 指定复杂属性值，以及甚至使用样式作为输入的其他样式。 有关详细信息，请参阅[样式设置和模板化](styling-and-templating.md)。  
  
3.  **样式属性值设置为资源：** 资源启用重用通常定义的对象和值的简单方法。 它是特别有用，可以定义使用的资源以使代码更加模块化的复杂值。 将以下突出显示的标记添加到 app.xaml。  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     直接在`Application.Resources`块中，创建名为"GrayBlueGradientBrush"的资源。 该资源定义水平渐变。 此资源可从任何位置的属性值作为应用程序，包括内部的按钮样式资源库中<xref:System.Windows.Controls.Control.Background%2A>属性。 现在，所有按钮都有<xref:System.Windows.Controls.Control.Background%2A>此渐变的属性值。  
  
     按 F5 运行该应用程序。 它应如以下所示。  
  
     ![具有渐变背景的按钮](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>创建用于定义按钮的外观的模板  
 在本部分中，你创建自定义按钮的外观 (presentation) 的模板。 按钮演示文稿是组成包括矩形和其他组件的多个对象提供独特外观的按钮。  
  
 到目前为止，应用程序中的按钮外观的控件已限制为更改按钮的属性。 如果你想要对按钮的外观进行更激进的更改？ 模板启用功能强大的对象显示的控制。 因为样式中，可以使用模板，您可以将模板应用于 （在本演练中，按钮），该样式应用到的所有对象。  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>若要使用模板来定义按钮的外观  
  
1.  **设置模板：** 因为的控件，如<xref:System.Windows.Controls.Button>具有<xref:System.Windows.Controls.Control.Template%2A>属性，可以定义模板属性值，就像我们已经设置了中的其他属性值一样<xref:System.Windows.Style>使用<xref:System.Windows.Setter>。 将以下突出显示的标记添加到按钮样式。  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  **更改按钮表示：** 此时，您需要定义模板。 添加以下突出显示的标记。 此标记指定了两个<xref:System.Windows.Shapes.Rectangle>元素具有圆角边缘、 后跟<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Controls.DockPanel>使用到主机<xref:System.Windows.Controls.ContentPresenter>的按钮。 一个<xref:System.Windows.Controls.ContentPresenter>显示按钮的内容。 在本演练中，内容是文本 （"按钮 1"、"按钮 2"、"Button 3"）。 所有模板组件 (矩形并<xref:System.Windows.Controls.DockPanel>) 内的布局<xref:System.Windows.Controls.Grid>。  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     按 F5 运行该应用程序。 它应如以下所示。  
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **将玻璃添加到模板：** 接下来将添加玻璃效果。 首先创建一些创建玻璃渐变效果的资源。 添加这些渐变中的资源任意位置`Application.Resources`块：  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />     
        <GradientStop Color="Transparent" Offset="0.4" />    
        <GradientStop Color="WhiteSmoke" Offset="0.5" />     
        <GradientStop Color="Transparent" Offset="0.75" />     
        <GradientStop Color="WhiteSmoke" Offset="0.9" />     
        <GradientStop Color="Transparent" Offset="1" />   
      </GradientStopCollection>   
      <LinearGradientBrush x:Key="MyGlassBrushResource"    
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     这些资源用作为<xref:System.Windows.Shapes.Shape.Fill%2A>矩形，我们将其插入到<xref:System.Windows.Controls.Grid>的按钮模板。 将以下突出显示的标记添加到模板。  
  
    ```xaml
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
          ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     
        <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       
          VerticalAlignment="Stretch"       
          StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       
          Fill="{StaticResource MyGlassBrushResource}"       
          RenderTransformOrigin="0.5,0.5">
          <Rectangle.Stroke>         
            <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">
              <LinearGradientBrush.GradientStops>
                <GradientStop Offset="0.0" Color="LightBlue" />
                <GradientStop Offset="1.0" Color="Gray" />
              </LinearGradientBrush.GradientStops>
            </LinearGradientBrush>       
          </Rectangle.Stroke>       
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->       
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
          <Rectangle.BitmapEffect>
            <BevelBitmapEffect />
          </Rectangle.BitmapEffect>
        </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     请注意，<xref:System.Windows.UIElement.Opacity%2A>与矩形的`x:Name`"glassCube"属性为 0，当您运行该示例，看不到玻璃矩形叠加在最前面。 这是因为我们将更高版本时添加触发器用于模板用户交互的按钮。 但是，可以看到该按钮如下所示现在通过更改<xref:System.Windows.UIElement.Opacity%2A>值与 1 和运行应用程序。 请参见下图。 在前进到下一步前, 更改<xref:System.Windows.UIElement.Opacity%2A>回 0。  
  
     ![通过使用 XAML 创建的自定义按钮](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>创建按钮交互性  
 在本部分中，将创建属性触发器和事件触发器可以更改属性值和运行动画以响应用户操作，例如将鼠标指针移动到按钮上方并单击。  
  
 添加交互性 （鼠标悬停、 鼠标离开，单击，等） 的简单方法是定义模板或样式中的触发器。 若要创建<xref:System.Windows.Trigger>，如定义属性"条件":按钮<xref:System.Windows.UIElement.IsMouseOver%2A>属性值等于`true`。 然后定义触发器条件为 true 时进行的资源库 （操作）。  
  
#### <a name="to-create-button-interactivity"></a>若要创建按钮交互性  
  
1.  **添加模板触发器：** 将突出显示的标记添加到你的模板。  
  
    ```xaml
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **添加属性触发器：** 添加到突出显示的标记`ControlTemplate.Triggers`块：  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     按 F5 以运行应用程序并查看效果，如对按钮运行鼠标指针。  
  
3.  **添加焦点触发器：** 接下来，我们将添加一些类似的 setter 来处理这种情况时该按钮具有焦点 （例如，在用户单击它）。  
  
    ```xaml  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     按 F5 以运行该应用程序并单击其中一个按钮。 请注意，在单击因为它仍然具有焦点的按钮始终保持突出显示。 如果单击另一个按钮，新建按钮获得焦点，而最后一个失去它。  
  
4.  **添加动画**<xref:System.Windows.UIElement.MouseEnter> **并** <xref:System.Windows.UIElement.MouseLeave> **:** 接下来我们将某些动画添加到触发器。 添加以下标记内部的任意位置`ControlTemplate.Triggers`块。  
  
    ```xaml
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     当鼠标指针移动到按钮上方并返回到正常大小当指针离开时，透明矩形会缩小。  
  
     当鼠标指针移到该按钮时触发的两个动画 (<xref:System.Windows.UIElement.MouseEnter>引发事件)。 这些动画收缩玻璃矩形沿 X 和 Y 轴。 请注意，属性在<xref:System.Windows.Media.Animation.DoubleAnimation>元素 —<xref:System.Windows.Media.Animation.Timeline.Duration%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定动画发生超过半秒，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>指定玻璃收缩 10%。  
  
     第二个事件触发器 (<xref:System.Windows.UIElement.MouseLeave>) 就会停止运行的第一个。 当您停止<xref:System.Windows.Media.Animation.Storyboard>，经过动画处理的所有属性都返回到其默认值。 因此，当用户移动指针离开按钮，按钮将恢复为之前在按钮上移动鼠标指针的方式。 有关动画的详细信息，请参阅[动画概述](../graphics-multimedia/animation-overview.md)。  
  
5.  **添加动画，以单击按钮时：** 最后一步是添加用于的触发器，当用户单击按钮。 添加以下标记内部的任意位置`ControlTemplate.Triggers`块：  
  
    ```xaml
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     按 F5 以运行该应用程序，并单击其中一个按钮。 当单击按钮时，透明矩形会旋转一周。  
  
## <a name="summary"></a>总结  
 在本演练中，您执行了以下练习：  
  
-   面向<xref:System.Windows.Style>为对象类型 (<xref:System.Windows.Controls.Button>)。  
  
-   控制在整个应用程序中使用的按钮的基本属性<xref:System.Windows.Style>。  
  
-   创建资源，如渐变来使用的属性值的<xref:System.Windows.Style>资源库。  
  
-   通过将模板应用于按钮自定义整个应用程序中的按钮的外观。  
  
-   自定义行为响应用户操作中的按钮 (如<xref:System.Windows.UIElement.MouseEnter>， <xref:System.Windows.UIElement.MouseLeave>，和<xref:System.Windows.Controls.Primitives.ButtonBase.Click>) 包含的动画效果。  
  
## <a name="see-also"></a>请参阅

- [使用 Microsoft Expression Blend 创建按钮](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [样式设置和模板化](styling-and-templating.md)
- [动画概述](../graphics-multimedia/animation-overview.md)
- [使用纯色和渐变进行绘制概述](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [位图效果概述](../graphics-multimedia/bitmap-effects-overview.md)
