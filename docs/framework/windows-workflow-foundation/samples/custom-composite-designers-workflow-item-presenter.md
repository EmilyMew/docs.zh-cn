---
title: 自定义复合设计器 — 工作流项演示器
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 4c1258a49ac3ef2227d520fe11f341819f8663a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089193"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>自定义复合设计器 — 工作流项演示器
<xref:System.Activities.Presentation.WorkflowItemPresenter>是可在何处可放置任意活动的"放置区"创建的 WF 设计器编程模型中的密钥类型。 此示例演示如何生成活动设计器呈现此类的"放置区。"

 此示例演示：

## <a name="demonstrates"></a>演示

-   使用 <xref:System.Activities.Presentation.WorkflowItemPresenter> 创建自定义活动设计器。

-   使用元数据存储区注册自定义设计器。

-   以声明方式和命令方式编程重新承载的工具箱。

## <a name="sample-details"></a>示例详细信息
 此示例的代码演示：

-   针对 `SimpleNativeActivity` 类生成自定义活动设计器。

-   使用 <xref:System.Activities.Presentation.WorkflowItemPresenter> 创建自定义活动设计器。

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 请注意，应使用 WPF 数据绑定来绑定到 `ModelItem.Body`。 `ModelItem` 该属性位于<xref:System.Activities.Presentation.ActivityDesigner>，是指在设计器正在使用，在这种情况下的基础对象**SimpleNativeActivity**。

#### <a name="to-setup-build-and-run-the-sample"></a>设置、生成和运行示例

1.  在 Visual Studio 2010 中打开的解决方案。

2.  按 F5 编译并运行应用程序。

> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>请参阅

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [使用工作流设计器开发应用程序](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
