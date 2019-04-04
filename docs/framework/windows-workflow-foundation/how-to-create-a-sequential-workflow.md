---
title: 如何：创建顺序工作流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 3991c16e00f1cbb4f8c1f2c8391f89ea51c1e6f2
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463795"
---
# <a name="how-to-create-a-sequential-workflow"></a>如何：创建顺序工作流
工作流可基于内置活动以及自定义活动来构造。 本主题将指导逐步创建如使用这两个内置的活动的工作流<xref:System.Activities.Statements.Sequence>活动，并从以前的自定义活动[如何：创建活动](how-to-create-an-activity.md)主题。 该工作流模拟猜数游戏。  
  
> [!NOTE]
>  入门教程中的每个主题都依赖于前面的主题。 若要完成本主题，必须先完成[如何：创建活动](how-to-create-an-activity.md)。  
  
> [!NOTE]
>  若要下载完整版教程，请参阅 [Windows Workflow Foundation (WF45) — 入门教程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
## <a name="to-create-the-workflow"></a>创建工作流  
  
1.  右键单击**NumberGuessWorkflowActivities**中**解决方案资源管理器**，然后选择**添加**，**新项**。  
  
2.  在中**已安装**，**常见项**节点中，选择**工作流**。 选择**活动**从**工作流**列表。  
  
3.  类型`SequentialNumberGuessWorkflow`成**名称**框，然后单击**添加**。  
  
4.  拖动**序列**活动从**控制流**一部分**工具箱**放到**在此处放置活动**上的标签工作流设计图面。  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a>创建工作流变量和自变量  
  
1.  双击**SequentialNumberGuessWorkflow.xaml**中**解决方案资源管理器**如果未显示在设计器中，显示工作流。  
  
2.  单击**自变量**左下角的工作流设计器，以显示**自变量**窗格。  
  
3.  单击**创建参数**。  
  
4.  类型`MaxNumber`成**名称**框中，选择**中**从**方向**下拉列表中，选择**Int32**从**自变量类型**下拉列表，然后按 ENTER 保存该自变量。  
  
5.  单击**创建参数**。  
  
6.  类型`Turns`成**名称**低于新添加的框`MaxNumber`参数中，选择**Out**从**方向**下拉列表中选择**Int32**从**自变量类型**下拉列表，然后按 ENTER。  
  
7.  单击**自变量**左下角的活动设计器，以关闭**自变量**窗格。  
  
8.  单击**变量**左下角的工作流设计器，以显示**变量**窗格。  
  
9. 单击**创建的变量**。  
  
    > [!TIP]
    >  如果没有**创建变量**显示框中，单击**序列**活动工作流设计器图面以将其选中。  
  
10. 类型`Guess`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
11. 单击**创建的变量**。  
  
12. 类型`Target`成**名称**框中，选择**Int32**从**变量类型**下拉列表，然后按 ENTER 保存该变量。  
  
13. 单击**变量**左下角的活动设计器，以关闭**变量**窗格。  
  
## <a name="to-add-the-workflow-activities"></a>添加工作流活动  
  
1.  拖动**分配**活动从**基元**一部分**工具箱**放到**序列**活动。 类型`Target`成**到**框中，以下表达式**输入 C# 表达式**或**输入 VB 表达式**框。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  如果**工具箱**不显示窗口中，选择**工具箱**从**视图**菜单。  
  
2.  拖动**DoWhile**活动从**控制流**一部分**工具箱**并将其放置在工作流，以便它低于**分配**活动。  
  
3.  将以下表达式键入**DoWhile**活动的**条件**属性值框。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <xref:System.Activities.Statements.DoWhile> 活动执行其子活动，然后计算其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。 如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 的计算结果为 `True`，则再次执行 <xref:System.Activities.Statements.DoWhile> 中的活动。 在此示例中，将计算用户的猜测值，并且 <xref:System.Activities.Statements.DoWhile> 继续执行，直到猜测值正确。  
  
4.  拖动**提示**活动从**NumberGuessWorkflowActivities**一部分**工具箱**并将其放置**DoWhile**活动从上一步。  
  
5.  在中**属性窗口**，类型`"EnterGuess"`包括引号**BookmarkName**属性值框**提示**活动。 类型`Guess`成**结果**属性值框中，并键入以下表达式**文本**属性框。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  如果**属性窗口**未显示，选择**属性窗口**从**视图**菜单。  
  
6.  拖动**分配**活动从**基元**部分**工具箱**并将其放置**DoWhile**活动以便它**提示**活动。  
  
    > [!NOTE]
    >  当 drop**分配**活动，请注意如何在工作流设计器会自动添加**序列**活动，使之同时包含**提示**活动和新添加**分配**活动。  
  
7.  类型`Turns`成**到**框和`Turns + 1`到**输入 C# 表达式**或**输入 VB 表达式**框。  
  
8.  拖动**如果**活动从**控制流**部分**工具箱**并将其放置**序列**活动以便它新添加的**分配**活动。  
  
9. 将以下表达式键入**如果**活动的**条件**属性值框。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. 将另一个**如果**活动从**控制流**一部分**工具箱**并将其放置**然后**部分中的第一个**如果**活动。  
  
11. 以下表达式键入新添加**如果**活动的**条件**属性值框。  
  
    ```
    Guess < Target  
    ```  
  
12. 将两个**WriteLine**中的活动**基元**部分**工具箱**并将它们放这样一个都位于**然后**部分新添加**如果**活动和一个处于**Else**部分。  
  
13. 单击**WriteLine**中的活动**然后**部分以选中它，并键入以下表达式**文本**属性值框。  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. 单击**WriteLine**中的活动**Else**部分以选中它，并键入以下表达式**文本**属性值框。  
  
    ```text
    "Your guess is too high."  
    ```  
  
     下面的示例说明了完成的工作流：  
  
     ![显示已完成的顺序工作流的屏幕截图。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a>生成工作流  
  
1.  按 Ctrl+Shift+B 生成解决方案。  
  
     有关如何运行工作流，说明，请参阅下一主题[如何：运行工作流](how-to-run-a-workflow.md)。 如果你已完成[如何：运行工作流](how-to-run-a-workflow.md)使用不同样式的工作流步骤并希望使用此步骤中的顺序工作流运行它，请直接跳转到[生成并运行应用程序](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一部分[如何：运行工作流](how-to-run-a-workflow.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 编程](programming.md)
- [设计工作流](designing-workflows.md)
- [入门教程](getting-started-tutorial.md)
- [如何：创建活动](how-to-create-an-activity.md)
- [如何：运行工作流](how-to-run-a-workflow.md)
