---
title: 演练：使用自定义组件自动填充工具箱
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: a1d138bcdc2c4637cd6aa035360ff258d3fe7100
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178784"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>演练：使用自定义组件自动填充工具箱
如果由当前打开的解决方案中的项目定义您的组件，它们将自动显示在**工具箱**，由你需执行任何操作。 可以手动填充**工具箱**与使用自定义组件[选择工具箱项对话框 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))，但**工具箱**考虑在解决方案中的项的生成包含所有以下特征的输出结果：  
  
-   实现<xref:System.ComponentModel.IComponent>;  
  
-   不具有<xref:System.ComponentModel.ToolboxItemAttribute>设置为`false`;  
  
-   不具有<xref:System.ComponentModel.DesignTimeVisibleAttribute>设置为`false`。  
  
> [!NOTE]
>  **工具箱**不遵循引用链，因此它将不显示并非由你的解决方案中的项目生成的项。  
  
 本演练演示如何自定义组件自动出现在**工具箱**生成组件后。 本演练涉及以下任务：  
  
-   创建一个 Windows 窗体项目。  
  
-   创建自定义组件。  
  
-   创建自定义组件的实例。  
  
-   卸载并重新加载自定义组件。  
  
 完成后，你将看到**工具箱**填充了已创建的组件。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建项目并设置窗体。  
  
#### <a name="to-create-the-project"></a>要创建项目  
  
1.  创建一个名为基于 Windows 的应用程序项目`ToolboxExample`(**文件** > **新建** > **项目** >  **Visual C#** 或**Visual Basic** > **经典桌面** > **Windows 窗体应用程序**)。  
  
2.  向项目添加新组件。 将其命名为 `DemoComponent`。  
  
     有关详细信息，请参阅[如何：添加新项目项](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。  
  
3.  生成项目。  
  
4.  从**工具**菜单上，单击**选项**项。 单击**常规**下**Windows 窗体设计器**项，然后确保**AutoToolboxPopulate**选项设置为**True**。  
  
## <a name="creating-an-instance-of-a-custom-component"></a>创建自定义组件的实例  
 下一步是在窗体上创建自定义组件的实例。 因为**工具箱**自动为新的组件的帐户，这非常简单，只创建任何其他组件或控件。  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>若要创建自定义组件的实例  
  
1.  打开中的项目的窗体**窗体设计器**。  
  
2.  在中**工具箱**，单击名为的新选项卡**ToolboxExample 组件**。  
  
     单击选项卡，会看到**DemoComponent**。  
  
    > [!NOTE]
    >  出于性能原因中的自动填充区域的组件**工具箱**不显示自定义位图和<xref:System.Drawing.ToolboxBitmapAttribute>不受支持。 若要显示的图标中的自定义组件**工具箱**，使用**选择工具箱项**对话框以加载该组件。  
  
3.  将组件拖到窗体上。  
  
     创建并添加到组件的实例**组件栏**。  
  
## <a name="unloading-and-reloading-a-custom-component"></a>卸载并重新加载自定义组件  
 **工具箱**项目，会考虑在每个组件的加载和卸载一个项目时，它会删除对项目的组件的引用。  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>尝试卸载和重新加载组件的工具箱上的效果  
  
1.  卸载该解决方案中的项目。  
  
     有关卸载的项目的详细信息，请参阅[如何：卸载并重新加载项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100))。 如果系统提示您保存时，选择**是**。  
  
2.  添加一个新**Windows 应用程序**到解决方案。 打开中的窗体**设计器**。  
  
     **ToolboxExample 组件**选项卡上一个项目现已消失了。  
  
3.  重新加载`ToolboxExample`项目。  
  
     **ToolboxExample 组件**选项卡现在再次出现。  
  
## <a name="next-steps"></a>后续步骤  
 本演练演示**工具箱**会考虑项目的组件，但**工具箱**同时也会考虑的控件。 通过添加和删除控件项目从解决方案来测试您自己的自定义控件。  
  
## <a name="see-also"></a>请参阅

- [“选项”对话框 ->“Windows 窗体设计器”->“常规”](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [如何：操作工具箱选项卡](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [选择工具箱项对话框 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [将控件放在 Windows 窗体上](putting-controls-on-windows-forms.md)
