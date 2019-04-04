---
title: 如何：创建使用现有服务协定的工作流服务
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 06d4d4f6687979f4fd54e919ca6f236a5b5402e8
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843003"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>如何：创建使用现有服务协定的工作流服务
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以协定优先工作流开发的形式实现了 Web 服务与工作流之间的更佳集成。 通过协定优先的工作流开发工具，可以在代码中优先设计协定。 然后该工具在工具箱中为协定中的操作自动生成活动模板。  
  
> [!NOTE]
>  本主题提供了有关创建协定优先工作流服务的分步指南。 有关协定优先工作流服务开发的详细信息，请参阅[协定优先工作流服务开发](contract-first-workflow-service-development.md)。  
  
### <a name="creating-the-workflow-project"></a>创建工作流项目  
  
1.  在 Visual Studio 中，选择**文件**，**新项目**。 选择**WCF**节点下的**C#** 中的节点**模板**树，然后选择**WCF 工作流服务应用程序**模板。  
  
2.  将新项目命名`ContractFirst`然后单击**确定**。  
  
### <a name="creating-the-service-contract"></a>创建服务协定  
  
1.  右键单击该项目中的**解决方案资源管理器**，然后选择**添加**，**新项...**. 选择**代码**左侧节点和**类**在右侧的模板。 将新类命名`IBookService`然后单击**确定**。  
  
2.  在显示的代码窗口的顶部，向 `System.Servicemodel` 添加一个 Using 语句。  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  将示例类定义更改为以下接口定义。  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  生成项目，通过按**Ctrl + Shift + B**。  
  
### <a name="importing-the-service-contract"></a>导入服务协定  
  
1.  右键单击该项目中的**解决方案资源管理器**，然后选择**导入服务协定**。 下 **\<当前项目>** ，打开所有子节点，然后选择 **IBookService** 。 单击 **“确定”**。  
  
2.  将会打开一个对话框，提示您该操作已成功完成，并且在生成该项目后，所生成的活动将出现在工具箱中。 单击 **“确定”**。  
  
3.  生成项目，通过按**Ctrl + Shift + B**，以便导入的活动将出现在工具箱中。  
  
4.  在中**解决方案资源管理器**，打开 Service1.xamlx。 该工作流服务将出现在设计器中。  
  
5.  选择**序列**活动。 在属性窗口中，单击 **...** 在按钮**ImplementedContract**属性。 在中**类型集合编辑器**出现窗口中，单击**类型**下拉列表中，并选择**浏览类型...** 项。 在中 **浏览并选择.NET 类型** 对话框下 **\<当前项目>** ，打开所有子节点，然后选择 **IBookService** 。 单击 **“确定”**。 在中**类型集合编辑器**对话框中，单击**确定**。  
  
6.  选择并删除**ReceiveRequest**并**SendResponse**活动。  
  
7.  从工具箱中拖动**Buy_ReceiveAndSendReply**和一个**Checkout_Receive**活动拖动到**顺序服务**活动。
