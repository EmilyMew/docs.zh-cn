---
title: 如何：使用 Windows Server App Fabric 的工作流服务主机
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 287067391f47a0b4bcbe11bd4bfab971954cd706
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465121"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>如何：使用 Windows Server App Fabric 的工作流服务主机
在 App Fabric 中承载工作流服务类似于在 IIS/WAS 下承载。 唯一的区别在于 App Fabric 提供的用于部署、监控和管理工作流服务的工具。 本主题使用工作流服务中创建[创建一个长时间运行的工作流服务](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)。 本主题将指导您创建工作流服务。 本主题将介绍如何使用 App Fabric 承载工作流服务。 有关 Windows Server App Fabric 的详细信息，请参阅[Windows Server App Fabric 文档](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)。 完成以下步骤之前，请确保已安装 Windows Server App Fabric。  为此，请打开 Internet Information Services (inetmgr.exe)，请单击您的服务器名称**连接**查看，单击站点，然后单击**Default Web Site**。 在屏幕的右侧，您应该看到一个名为部分**App Fabric**。 如果您看不到这一部分（它位于右侧窗格的顶部），则表示您还未安装 App Fabric。 有关安装 Windows Server App Fabric 的详细信息请参阅[安装 Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136)。  
  
### <a name="creating-a-simple-workflow-service"></a>创建简单工作流服务  
  
1.  打开 Visual Studio 2012 并加载您在中创建的 OrderProcessing 解决方案[创建一个长时间运行的工作流服务](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)主题。  
  
2.  右键单击**OrderService**项目，然后选择**属性**，然后选择**Web**选项卡。  
  
3.  在中**启动操作**部分的属性页，选择**特定页**编辑框中键入 Service1.xamlx。  
  
4.  在中**服务器**部分的属性页，选择**使用本地 IIS Web 服务器**并键入以下 URL: `http://localhost/OrderService`。  
  
5.  单击**创建虚拟目录**按钮。 这将新建一个虚拟目录，并将项目设置为在生成项目时将所需文件复制到此虚拟目录。  或者，你也可以手动将 .xamlx、web.config 以及任何所需的 DLL 复制到此虚拟目录。  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>配置承载于 Windows Server App Fabric 中的工作流服务  
  
1.  打开 Internet 信息服务管理器 (inetmgr.exe)。  
  
2.  导航到 OrderService 虚拟目录中**连接**窗格。  
  
3.  右击 OrderService 并选择**管理 WCF 和 WF 服务**，**配置...**. **为应用程序配置 WCF 和 WF**显示对话框。  
  
4.  选择**常规**选项卡以显示有关应用程序的常规信息，如以下屏幕截图中所示。  
  
     ![App Fabric 配置对话框常规选项卡](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-常规")  
  
5.  选择**监视**选项卡。这将显示各种监控设置，如下面的屏幕快照所示。  
  
     ![App Fabric 配置监视选项卡](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration 监视")  
  
     有关配置工作流服务的详细信息中 App Fabric 监视请参阅[配置使用 App Fabric 监视](https://go.microsoft.com/fwlink/?LinkId=193153)。  
  
6.  选择**工作流持久性**选项卡。这样，您可以将应用程序配置为使用 App Fabric 的默认暂留提供程序，如下面的屏幕快照所示。  
  
     ![App Fabric 配置&#45;持久性](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration 暂留")  
  
     有关在 Windows Server App Fabric 中配置工作流持久性的详细信息请参阅[App Fabric 中配置工作流持久性](https://go.microsoft.com/fwlink/?LinkId=193148)。  
  
7.  选择**工作流主机管理**选项卡。这样，您可以指定何时应卸载和暂留空闲的工作流服务实例，如下面的屏幕快照所示。  
  
     ![应用程序结构配置工作流主机管理](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration 管理")  
  
     有关工作流主机管理配置的详细信息请参阅[App Fabric 中配置工作流主机管理](https://go.microsoft.com/fwlink/?LinkId=193151)。  
  
8.  选择**自动启动**选项卡。这样，您可以为应用程序中的工作流服务指定自动启动设置，如下面的屏幕快照所示。  
  
     ![显示应用 Fabric 自动的屏幕截图&#45;启动配置。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     有关配置自动启动的详细信息请参阅[使用 App Fabric 配置的自动启动](https://go.microsoft.com/fwlink/?LinkId=193150)。  
  
9. 选择**限制**选项卡。这样，您可以为工作流服务配置限制设置，如下面的屏幕快照所示。  
  
     ![显示限制配置 App Fabric 的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     有关配置限制的详细信息请参阅[使用 App Fabric 配置限制](https://go.microsoft.com/fwlink/?LinkId=193149)。  
  
10. 选择**安全**选项卡。这样，您可以为应用程序配置安全设置，如下面的屏幕快照所示。  
  
     ![App Fabric 安全配置](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration 安全")  
  
     有关使用 Windows Server App Fabric 配置安全性的详细信息请参阅[使用 App Fabric 配置安全性](https://go.microsoft.com/fwlink/?LinkId=193152)。  
  
### <a name="using-windows-server-app-fabric"></a>使用 Windows Server App Fabric  
  
1.  生成解决方案以便将所需的文件复制到虚拟目录。  
  
2.  右键单击 OrderClient 项目，然后选择**调试**，**启动新实例**启动客户端应用程序。  
  
3.  客户端的运行时间以及 Visual Studio 将显示**附加安全警告**对话框中，单击**不附加**按钮。 这会告知 Visual Studio 不要附加到 IIS 进程进行调试。  
  
4.  客户端应用程序将立即调用工作流服务，然后等待。 工作流服务将转为空闲暂留状态。 通过启动 Internet 信息服务 (inetmgr.exe)，在“连接”窗格中导航至 OrderService 并将其选中，可以对此进行验证。 接下来，单击右侧窗格中的“App Fabric 仪表板”图标。 在“暂留的 WF 实例”下，您将看到存在一个暂留的工作流服务实例，如下面的屏幕快照所示。  
  
     ![显示 App Fabric 仪表板的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **WF 实例历史记录**列出有关工作流服务工作流服务激活次数、 工作流服务实例的完成数目和工作流实例的失败数等信息。 在活动或空闲实例下将显示一个链接，单击此链接将显示更多有关空闲工作流实例的信息，如下面的屏幕快照所示。  
  
     ![显示持久保存工作流实例详细信息的屏幕截图。](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     详细了解 Windows Server App Fabric 功能以及如何使用它们查看[Windows Server App Fabric 承载功能](https://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>请参阅
- [创建长时间运行的工作流服务](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Windows Server App Fabric 承载功能](https://go.microsoft.com/fwlink/?LinkId=193143)
- [安装 Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136)
- [Windows Server App Fabric 文档](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
