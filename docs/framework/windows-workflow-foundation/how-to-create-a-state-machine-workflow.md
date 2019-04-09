---
title: 如何：创建状态机工作流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 564e9e424b8b82e8837a0a58cb8c11389920c297
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139628"
---
# <a name="how-to-create-a-state-machine-workflow"></a>如何：创建状态机工作流
工作流可基于内置活动以及自定义活动来构造。 本主题将指导逐步创建如使用这两个内置的活动的工作流<xref:System.Activities.Statements.StateMachine>活动，并从以前的自定义活动[如何：创建活动](how-to-create-an-activity.md)主题。 该工作流模拟猜数游戏。  
  
> [!NOTE]
>  入门教程中的每个主题都依赖于前面的主题。 若要完成本主题，必须先完成[如何：创建活动](how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下载完整版教程，请参阅 [Windows Workflow Foundation (WF45) — 入门教程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>创建工作流  
  
1.  右键单击**NumberGuessWorkflowActivities**中**解决方案资源管理器**，然后选择**添加**，**新项**。  
  
2.  在中**已安装**，**常见项**节点中，选择**工作流**。 选择**活动**从**工作流**列表。  
  
3.  类型`StateMachineNumberGuessWorkflow`成**名称**框，然后单击**添加**。  
  
4.  拖动**StateMachine**活动从**状态机**一部分**工具箱**放到**在此处放置活动**上的标签工作流设计图面。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>创建工作流变量和自变量  
  
1.  双击**StateMachineNumberGuessWorkflow.xaml**中**解决方案资源管理器**如果未显示在设计器中，显示工作流。  
  
2.  单击**自变量**左下角的工作流设计器，以显示**自变量**窗格。  
  
3.  单击**创建参数**。  
  
4.  类型`MaxNumber`成**名称**框中，选择**中**从**方向**下拉列表中，选择**Int32**从**自变量类型**下拉列表，然后按 ENTER 保存该自变量。  
  
5.  单击**创建参数**。  
  
6.  类型`Turns`成**名称**低于新添加的框`MaxNumber`参数中，选择**Out**从**方向**下拉列表中选择**Int32**从**自变量类型**下拉列表，然后按 ENTER。  
  
7.  单击**自变量**左下角的活动设计器，以关闭**自变量**窗格。  
  
8.  单击**变量**左下角的工作流设计器，以显示**变量**窗格。  
  
9. 单击**创建的变量**。  
  
    > [!TIP]
    >  如果没有**创建变量**框中显示，请单击<xref:System.Activities.Statements.StateMachine>活动工作流设计器图面以将其选中。  
  
10. 类型`Guess`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
11. 单击**创建的变量**。  
  
12. 类型`Target`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
13. 单击**变量**左下角的活动设计器，以关闭**变量**窗格。  
  
### <a name="to-add-the-workflow-activities"></a>添加工作流活动  
  
1.  单击**State1**以将其选中。 在中**属性窗口**，更改**DisplayName**到`Initialize Target`。  
  
    > [!TIP]
    >  如果**属性窗口**未显示，选择**属性窗口**从**视图**菜单。  
  
2.  双击刚刚重命名**Initialize Target**状态处于工作流设计器，以将其展开。  
  
3.  拖动**分配**活动从**基元**一部分**工具箱**放到**条目**状态的部分。 类型`Target`成**到**框中，以下表达式**输入 C# 表达式**或**输入 VB 表达式**框。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**不显示窗口中，选择**工具箱**从**视图**菜单。  
  
4.  返回到整体状态机工作流设计器中的视图，通过单击**StateMachine**痕迹导航中显示在工作流设计器的顶部。  
  
5.  拖动**状态**活动从**状态机**一部分**工具箱**拖到工作流设计器并将它悬停**Initialize Target**状态。 请注意周围会出现四个三角形**Initialize Target**新状态位于其上方时的状态。 下面是立即的三角形上新的状态放**Initialize Target**状态。 这将放置到工作流的新状态，并创建从过渡**Initialize Target**状态到新状态。  
  
6.  单击**State1**以选择它，更改**DisplayName**到`Enter Guess`，然后双击以将其展开工作流设计器中的状态。  
  
7.  拖动**WriteLine**活动从**基元**一部分**工具箱**放到**条目**状态的部分。  
  
8.  将以下表达式键入**文本**属性框**WriteLine**。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 拖动**分配**活动从**基元**一部分**工具箱**拖放**退出**状态的部分。  
  
10. 类型`Turns`成**到**框和`Turns + 1`到**输入 C# 表达式**或**输入 VB 表达式**框。  
  
11. 返回到整体状态机工作流设计器中的视图，通过单击**StateMachine**痕迹导航中显示在工作流设计器的顶部。  
  
12. 拖动**FinalState**活动从**状态机**一部分**工具箱**，通过将鼠标悬停在**Enter Guess**状态，并将其放上的右侧显示的三角形**Enter Guess**状态，以便之间创建转换**Enter Guess**并**FinalState**。  
  
13. 过渡的默认名称是**T2**。 单击以选中它，并设置工作流设计器中的该转换将其**DisplayName**到**Guess Correct**。 然后单击并选择**FinalState**，并将其拖到右侧，以便为完整的转换名称，而不会覆盖两种状态之一显示留出空间。 这样可以方便完成本教程中的剩余步骤。  
  
14. 双击刚刚重命名**Guess Correct**转换中工作流设计器，以将其展开。  
  
15. 拖动**ReadInt**活动从**NumberGuessWorkflowActivities**一部分**工具箱**并将其放置**触发器**部分转换。  
  
16. 在中**属性窗口**有关**ReadInt**活动中，键入`"EnterGuess"`包括引号**BookmarkName**属性值框，然后键入`Guess`成**结果**属性值框  
  
17. 将以下表达式键入**Guess Correct**转换的**条件**属性值框。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 返回到整体状态机工作流设计器中的视图，通过单击**StateMachine**痕迹导航中显示在工作流设计器的顶部。  
  
    > [!NOTE]
    >  当收到触发器事件和 <xref:System.Activities.Statements.Transition.Condition%2A>（如果存在）时，将发生转换，计算结果为 `True`。 对于此转换，如果用户的`Guess`匹配随机生成`Target`，则将控制传递到**FinalState**和工作流完成。  
  
19. 根据猜测是否正确，工作流应转换到**FinalState**或回**输入猜测**另一次尝试的状态。 这两个转换共享同一触发器，等待用户的猜测，若要通过接收**ReadInt**活动。 这称为共享转换。 若要创建共享的转换，请单击圆圈，以指示开头**Guess Correct**转换并将其拖到所需的状态。 在这种情况下转换属自行转换，因此拖动的起点**Guess Correct**过渡并将其放回的底部**Enter Guess**状态。 在创建转换，在工作流设计器中选择它并设置其**DisplayName**属性设置为**Guess Incorrect**。  
  
    > [!NOTE]
    >  共享的转换还可以创建从在转换设计器通过单击**添加共享的触发器转换**底部的转换设计器，然后选择所需的目标状态从**若要连接的可用状态**下拉列表。  
  
    > [!NOTE]
    >  注意，如果转换的 <xref:System.Activities.Statements.Transition.Condition%2A> 计算结果为 `false`（或所有共享触发转换条件的计算结果均为 `false`），转换将不发生，并且此状态下的所有转换的所有触发将被重新计划。 在本教程中，由于配置条件的方式，这种情况不会发生（我们针对猜测是正确或者错误提供了具体的操作）。  
  
20. 双击**Guess Incorrect**转换中工作流设计器，以将其展开。 请注意，**触发器**已设置为相同**ReadInt**使用的活动**Guess Correct**转换。  
  
21. 将以下表达式键入**条件**属性值框。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 拖动**如果**活动从**控制流**一部分**工具箱**拖放**操作**过渡的部分。  
  
23. 将以下表达式键入**如果**活动的**条件**属性值框。  
  
    ```
    Guess < Target  
    ```  
  
24. 将两个**WriteLine**中的活动**基元**部分**工具箱**并将它们放这样一个都位于**然后**部分**如果**活动和一个处于**Else**部分。  
  
25. 单击**WriteLine**中的活动**然后**部分以选中它，并键入以下表达式**文本**属性值框。  
  
    ```
    "Your guess is too low."  
    ```  
  
26. 单击**WriteLine**中的活动**Else**部分以选中它，并键入以下表达式**文本**属性值框。  
  
    ```
    "Your guess is too high."  
    ```  
  
27. 返回到整体状态机工作流设计器中的视图，通过单击**StateMachine**痕迹导航中显示在工作流设计器的顶部。  
  
     下面的示例阐释已完成的工作流。  
  
     ![完整的状态机工作流](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>生成工作流  
  
1.  按 Ctrl+Shift+B 生成解决方案。  
  
     有关如何运行工作流，说明，请参阅下一主题[如何：运行工作流](how-to-run-a-workflow.md)。 如果你已完成[如何：运行工作流](how-to-run-a-workflow.md)使用不同样式的工作流步骤并希望使用此步骤中的状态机工作流运行它，请直接跳转到[生成并运行应用程序](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一部分[如何：运行工作流](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 编程](programming.md)
- [设计工作流](designing-workflows.md)
- [入门教程](getting-started-tutorial.md)
- [如何：创建活动](how-to-create-an-activity.md)
- [如何：运行工作流](how-to-run-a-workflow.md)
