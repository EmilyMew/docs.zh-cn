---
title: 创建长时间运行的工作流服务
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 37d3accae017b6725eab5ebb3d7df6e1bc15a56a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109650"
---
# <a name="creating-a-long-running-workflow-service"></a>创建长时间运行的工作流服务
本主题描述如何创建长时间运行的工作流服务。 长时间运行的工作流服务可能会运行很长一段时间。 在某一时刻，工作流可能会转入空闲状态，等待一些附加信息。 当这种情况发生时，工作流将保存到 SQL 数据库并从内存中删除。 当附加信息变得可用时，工作流实例将重新加载回内存，继续执行。  在此方案中，您将实现一个非常简化的订单系统。  客户端向工作流服务发送初始消息以启动订单。 此服务将订单 ID 返回给客户端。 此时，工作流服务要等待来自客户端的另一条消息，它转入空闲状态并保存到 SQL Server 数据库。  当客户端发送下一条消息订购项目时，工作流服务将重新加载回内存，完成处理此订单。 在代码示例中它将返回一个字符串，指示项目已添加到订单中。 代码示例并不是技术的现实应用，而是作为一个简单的示例来说明长时间运行的工作流服务。 本主题假定你知道如何创建 Visual Studio 2012 项目和解决方案。

## <a name="prerequisites"></a>系统必备
 您必须安装了下列软件才能使用本演练：

1.  Microsoft SQL Server 2008

2.  Visual Studio 2012

3.  Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4.  您熟悉 WCF 和 Visual Studio 2012，并且知道如何创建项目/解决方案。

### <a name="to-setup-the-sql-database"></a>设置 SQL 数据库

1.  为了使工作流服务实例能够持久化，您必须安装 Microsoft SQL Server，并配置一个数据库来存储持久化工作流实例。 通过单击运行 Microsoft SQL Management Studio**启动**按钮，选择**所有程序**， **Microsoft SQL Server 2008**，和**Microsoft SQLManagement Studio**。

2.  单击**Connect**按钮以登录到 SQL Server 实例

3.  右键单击**数据库**在树视图中，选择**新建数据库...** 若要创建名为的新数据库`SQLPersistenceStore`。

4.  在 SQLPersistenceStore 数据库上运行位于 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目录中的 SqlWorkflowInstanceStoreSchema.sql 脚本文件，以设置所需的数据库架构。

5.  在 SQLPersistenceStore 数据库上运行位于 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目录中的 SqlWorkflowInstanceStoreLogic.sql 脚本文件，以设置所需的数据库逻辑。

### <a name="to-create-the-web-hosted-workflow-service"></a>创建 Web 承载的工作流服务

1.  创建空的 Visual Studio 2012 解决方案，将其命名`OrderProcessing`。

2.  向该解决方案添加一个名为 `OrderService` 的新 WCF 工作流服务应用程序项目。

3.  在项目属性对话框中，选择**Web**选项卡。

    1.  下**启动操作**选择**特定页**并指定`Service1.xamlx`。

         ![工作流服务项目 Web 属性](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "创建 web 承载的工作流服务-特定页选项")

    2.  下**服务器**选择**使用本地 IIS Web 服务器**。

         ![本地 Web 服务器设置](./media/creating-a-long-running-workflow-service/use-local-web-server.png "创建 web 承载的工作流服务-使用本地 IIS Web 服务器选项")

        > [!WARNING]
        >  在管理员模式下才能进行此设置，必须运行 Visual Studio 2012。

         这两个步骤将工作流服务项目配置为由 IIS 承载。

4.  打开`Service1.xamlx`是否不已打开，并删除现有**ReceiveRequest**并**SendResponse**活动。

5.  选择**顺序服务**活动，然后单击**变量**链接，然后添加以下插图所示的变量。 通过执行此操作，会添加一些稍后将在工作流服务中使用的变量。

    > [!NOTE]
    >  如果 CorrelationHandle 不在变量类型下拉列表中，选择**浏览类型**从下拉列表。 键入在 CorrelationHandle**类型名称**框中，从列表框中选择 CorrelationHandle 并单击**确定**。

     ![将变量添加](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "将变量添加到顺序服务活动。")

6.  拖放到**ReceiveAndSendReply**到活动模板**顺序服务**活动。 这组活动将接收来自客户端的消息，并发送回复。

    1.  选择**接收**活动，并在下图中突出显示的属性的设置。

         ![设置接收活动属性](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "设置 Receive 活动属性。")

         DisplayName 属性设置在设计器中显示的 Receive 活动的名称。 ServiceContractName 和 OperationName 属性指定 Receive 活动实现的服务协定和操作的名称。 有关如何在工作流服务中使用协定的详细信息请参阅[在工作流中使用协定](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。

    2.  单击**定义...** 中的链接**ReceiveStartOrder**活动和设置如下图中显示的属性。  请注意，**参数**单选按钮处于选中状态，名为的参数`p_customerName`绑定到`customerName`变量。 这会配置**接收**活动接收某种数据并将该数据绑定到本地变量。

         ![设置由 Receive 活动接收的数据](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "设置由 Receive 活动接收的数据的属性。")

    3.  选择**SendReplyToReceive**活动，并设置突出显示的属性在下图中所示。

         ![设置 SendReply 活动属性](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4.  单击**定义...** 中的链接**SendReplyToStartOrder**活动和设置如下图中显示的属性。 请注意，**参数**单选按钮处于选中状态; 参数名为`p_orderId`绑定到`orderId`变量。 此设置指定 SendReplyToStartOrder 活动将类型字符串的值返回给调用方。

         ![配置 SendReply 活动内容数据](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "为 SetReplyToStartOrder 活动配置设置。")

    5.  拖放 Assign 活动之间**接收**并**SendReply**活动并设置属性，如以下插图所示：

         ![添加 assign 活动](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "添加 assign 活动。")

         这将创建一个新的订单 ID，并将该值放在 orderId 变量中。

    6.  选择**replytostartorder**活动。 在属性窗口中单击省略号按钮**相关初始值设定项**。 选择**添加初始值设定项**链接，输入`orderIdHandle`在初始值设定项文本框中，选择查询相关初始值设定项为相关类型，然后选择 p_orderId XPATH 查询下拉列表框的。 这些设置如下图所示。 单击 **“确定”**。  这将初始化客户端与此工作流服务实例之间的相关性。 当接收到包含此订单 ID 的消息时，将该消息路由至此工作流服务实例。

         ![添加相关初始值设定项](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "添加相关初始值设定项。")

7.  拖放另一个**ReceiveAndSendReply**到工作流的末尾的活动 (外部**序列**包含第一个**接收**和**SendReply**活动)。 这将接收客户端发送的第二条消息，并对它做出响应。

    1.  选择**序列**，其中包含新添加**接收**并**SendReply**活动，然后单击**变量**按钮。 添加下图中突出显示的变量：

         ![添加新变量](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "添加 ItemId 变量。")

    2.  选择**接收**活动和设置如下图中显示的属性：

         ![设置 Receive 活动属性](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "设置 Receive 活动属性。")

    3.  单击**定义...** 中的链接**ReceiveAddItem**活动并添加以下插图所示的参数： 这会配置接收活动接受两个参数，即订单 ID 和正在排序的项的 ID。

         ![为第二次接收指定参数](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "配置 receive 活动接收两个参数。")

    4.  单击**correlateon**省略号按钮，然后输入`orderIdHandle`。 下**XPath 查询**，单击向下箭头并选择`p_orderId`。 这将对第二个接收活动配置相关性。 有关相关的详细信息请参阅[相关](../../../../docs/framework/wcf/feature-details/correlation.md)。

         ![设置 CorrelatesOn 属性](./media/creating-a-long-running-workflow-service/correlateson-setting.png "设置 CorrelatesOn 属性。")

    5.  拖放到**如果**活动后立即**ReceiveAddItem**活动。 此活动的行为与 if 语句类似。

        1.  设置**条件**属性 `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2.  拖放到**分配**到中的活动**然后**部分，另一个到**Else**部分设置的属性**分配**下图中所示的活动。

             ![将服务调用的结果分配](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "分配服务调用的结果。")

             如果条件为`true`**然后**将执行部分。 如果条件为`false` **Else**执行部分。

        3.  选择**SendReplyToReceive**活动，并设置**DisplayName**属性在下图中所示。

             ![设置 SendReply 活动属性](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "设置 SendReply 活动属性。")

        4.  单击**定义...** 中的链接**SetReplyToAddItem**活动并将其配置，如下图中所示。 这会配置**sendreplytoadditem**活动中的值返回`orderResult`变量。

             ![设置 SendReply 活动的数据绑定](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "设置为 sendreplytoadditem 活动的属性。")

8.  打开 web.config 文件并添加以下元素中的\<行为 > 节，以启用工作流持久性。

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  确保替换上面代码段中的主机和 SQL Server 实例名称。

9. 生成解决方案。

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>创建客户端应用程序以调用工作流服务

1.  将一个名为 `OrderClient` 的新控制台应用程序项目添加到解决方案中。

2.  向 `OrderClient` 项目中添加对以下程序集的引用：

    1.  System.ServiceModel.dll

    2.  System.ServiceModel.Activities.dll

3.  添加对工作流服务的服务引用，并将 `OrderService` 指定为命名空间。

4.  在客户端项目的 `Main()` 方法中，添加以下代码：

    ```
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5.  生成解决方案，并运行 `OrderClient` 应用程序。 客户端将显示以下文本：

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6.  若要验证是否已持久保存工作流服务，请启动 SQL Server Management Studio，通过转到**启动**菜单中，选择**所有程序**， **Microsoft SQL Server 2008**， **SQL Server Management Studio**。

    1.  在左侧窗格中展开**数据库**， **SQLPersistenceStore**，**视图**，然后右键单击**System.Activities.DurableInstancing.Instances** ，然后选择**选择前 1000年行**。 在中**结果**窗格中，确认你看到列出的至少一个实例。 如果运行时出现异常，则可能存在先前运行的其他实例。 通过右键单击可以删除现有行**System.Activities.DurableInstancing.Instances** ，然后选择**编辑前 200 行**，按**Execute**按钮，在结果窗格中选择所有行并都选择**删除**。  若要验证数据库中显示的实例是否为应用程序创建的实例，请在运行客户端之前验证实例视图是否为空。 客户端开始运行后，重新运行查询（选择前 1000 行），并确认已添加新实例。

7.  按 Enter 将添加项目消息发送至工作流服务。 客户端将显示以下文本：

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>请参阅

- [工作流服务](../../../../docs/framework/wcf/feature-details/workflow-services.md)
