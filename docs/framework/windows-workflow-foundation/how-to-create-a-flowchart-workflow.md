---
title: 如何：创建 Flowchart 工作流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 1da81ae47fa9f74b6037b6fcec4dbac5350c4481
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080236"
---
# <a name="how-to-create-a-flowchart-workflow"></a>如何：创建 Flowchart 工作流
工作流可基于内置活动以及自定义活动来构造。 本主题将指导逐步创建如使用这两个内置的活动的工作流<xref:System.Activities.Statements.Flowchart>活动，并从以前的自定义活动[如何：创建活动](how-to-create-an-activity.md)主题。 该工作流模拟猜数游戏。  
  
> [!NOTE]
>  入门教程中的每个主题都依赖于前面的主题。 若要完成本主题，必须先完成[如何：创建活动](how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下载完整版教程，请参阅 [Windows Workflow Foundation (WF45) — 入门教程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>创建工作流  
  
1.  右键单击**NumberGuessWorkflowActivities**中**解决方案资源管理器**，然后选择**添加**，**新项**。  
  
2.  在中**已安装**，**常见项**节点中，选择**工作流**。 选择**活动**从**工作流**列表。  
  
3.  类型`FlowchartNumberGuessWorkflow`成**名称**框，然后单击**添加**。  
  
4.  拖动**流程图**活动从**流程图**一部分**工具箱**放到**在此处放置活动**上的标签工作流设计图面。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>创建工作流变量和自变量  
  
1.  双击**FlowchartNumberGuessWorkflow.xaml**中**解决方案资源管理器**如果未显示在设计器中，显示工作流。  
  
2.  单击**自变量**左下角的工作流设计器，以显示**自变量**窗格。  
  
3.  单击**创建参数**。  
  
4.  类型`MaxNumber`成**名称**框中，选择**中**从**方向**下拉列表中，选择**Int32**从**自变量类型**下拉列表，然后按 ENTER 保存该自变量。  
  
5.  单击**创建参数**。  
  
6.  类型`Turns`成**名称**低于新添加的框`MaxNumber`参数中，选择**Out**从**方向**下拉列表中选择**Int32**从**自变量类型**下拉列表，然后按 ENTER。  
  
7.  单击**自变量**左下角的活动设计器，以关闭**自变量**窗格。  
  
8.  单击**变量**左下角的工作流设计器，以显示**变量**窗格。  
  
9. 单击**创建的变量**。  
  
    > [!TIP]
    >  如果没有**创建变量**框中显示，请单击<xref:System.Activities.Statements.Flowchart>活动工作流设计器图面以将其选中。  
  
10. 类型`Guess`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
11. 单击**创建的变量**。  
  
12. 类型`Target`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
13. 单击**变量**左下角的活动设计器，以关闭**变量**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>添加工作流活动  
  
1.  拖动**分配**活动从**基元**部分**工具箱**并将它悬停**启动**节点，即在顶部流程图。 当**分配**活动位于**启动**节点，周围会出现三个三角形**启动**节点。 Drop**分配**下方的三角形上的活动**启动**节点。 这将两个项一起链接并将指定**分配**流程图中的第一个活动的活动。  
  
    > [!NOTE]
    >  也还可以通过手动将活动链接到开始节点而将活动指示为流程图中的起始活动。 若要执行此操作，将鼠标悬停**启动**节点中，单击鼠标位于上方时出现的矩形之一**启动**节点，，然后将连接至所需的活动并将其放置在其中一个出现的矩形。 您还可以指定一个活动为起始活动通过右键单击并选择**设置为开始节点**。  
  
2.  类型`Target`成**到**框中，以下表达式**输入 C# 表达式**或**输入 VB 表达式**框。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**不显示窗口中，选择**工具箱**从**视图**菜单。  
  
3.  拖动**提示**活动从**NumberGuessWorkflowActivities**一部分**工具箱**，删除以下**分配**活动从上一个步骤，并连接**Prompt**活动**分配**活动。 可通过三种方法来连接这两个活动。 第一种方法是将它们连接，如拖放**提示**上工作流的活动。 如您拖动**Prompt**到工作流活动悬停**分配**活动放到出现时的四个三角形之一**提示**活动是通过**分配**活动。 第二种方法是删除**提示**活动拖动到所需的位置处的工作流。 然后，将鼠标悬停**分配**活动，并将其中一个向下出现的矩形**提示**活动。 拖动鼠标，使连接线从**分配**活动连接到的矩形之一**提示**活动，然后松开鼠标按钮。 第三种方法是非常类似于第一种方法，不同之处在于而不是拖动**Prompt**活动从**工具箱**，将其从其位置拖动工作流设计图面上，悬停**分配**活动，放到出现的三角形之一。  
  
4.  在中**属性窗口**有关**提示**活动中，键入`"EnterGuess"`包括引号**BookmarkName**属性值框。 类型`Guess`成**结果**属性值框中，并键入以下表达式**文本**属性框。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果**属性窗口**未显示，选择**属性窗口**从**视图**菜单。  
  
5.  拖动**分配**活动从**基元**一部分**工具箱**并将其使用，以便它低于上一步中所述的方法之一连接**提示**活动。  
  
6.  类型`Turns`成**到**框和`Turns + 1`到**输入 C# 表达式**或**输入 VB 表达式**框。  
  
7.  拖动**FlowDecision**从**流程图**一部分**工具箱**并将其连接下**分配**活动。 在中**属性窗口**，键入以下表达式**条件**属性值框。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  将另一个**FlowDecision**活动从**工具箱**并将其放置第一个文本框下方。 连接两个活动通过将从标记为的矩形拖**False**顶部**FlowDecision**向该矩形顶部的第二个活动**FlowDecision**活动。  
  
    > [!TIP]
    >  如果没有看到 **，则返回 True**并**False**标签上**FlowDecision**，将鼠标悬停**FlowDecision**。  
  
9. 单击第二个**FlowDecision**活动以选择它。 在中**属性窗口**，键入以下表达式**条件**属性值框。  
  
    ```
    Guess < Target  
    ```  
  
10. 将两个**WriteLine**中的活动**基元**一部分**工具箱**并将它们放以便并排显示两个**FlowDecision**活动。 连接 **，则返回 True**操作的底部**FlowDecision**到最左边的活动**WriteLine**活动中，并**False**操作保存到最右侧**WriteLine**活动。  
  
11. 单击最左边**WriteLine**活动以选择它，并键入以下表达式**文本**属性值框中**属性窗口**。  
  
    ```
    "Your guess is too low."  
    ```  
  
12. 连接**WriteLine**左侧和右侧的向**提示**其上面的活动。  
  
13. 单击最右侧**WriteLine**活动以选择它，并键入以下表达式**文本**属性值框中**属性窗口**。  
  
    ```
    "Your guess is too high."  
    ```  
  
14. 连接**WriteLine**活动的右侧**提示**其上方的活动。  
  
     下面的示例阐释已完成的工作流。  
  
     ![完成 Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>生成工作流  
  
1.  按 Ctrl+Shift+B 生成解决方案。  
  
     有关如何运行工作流，说明，请参阅下一主题[如何：运行工作流](how-to-run-a-workflow.md)。 如果你已完成[如何：运行工作流](how-to-run-a-workflow.md)使用不同样式的工作流步骤并希望使用此步骤中的流程图工作流运行它，请直接跳转到[生成并运行应用程序](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一部分[如何：运行工作流](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 编程](programming.md)
- [设计工作流](designing-workflows.md)
- [入门教程](getting-started-tutorial.md)
- [如何：创建活动](how-to-create-an-activity.md)
- [如何：运行工作流](how-to-run-a-workflow.md)
