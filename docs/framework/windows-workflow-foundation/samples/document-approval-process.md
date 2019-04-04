---
title: 文档审批过程
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 4451719bfb1d46a4e0e4dcde19666d1f8b2de427
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409544"
---
# <a name="document-approval-process"></a>文档审批过程
此示例演示在一起的多个 Windows Workflow Foundation (WF) 和 Windows Communication Foundation (WCF) 功能的使用。 这些功能一起使用实现一个文档审批过程方案。 客户端应用程序既可提交等待审批的文档，也可批准文档。 有一个审批管理器应用程序，可用于促进客户端之间的通信和强制执行审批过程的规则。 审批过程是一个可执行多种类型的审批的工作流。 存在多个活动来获取个人审批过程、团体审批过程（一定百分比的审批者）和复合审批过程（由团体审批和个人审批按顺序组成）。

> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>示例详细信息  
 下图演示文档审批过程工作流：  
  
 ![文档审批进程工作流](./media/document-approval-process/document-approval-process.jpg)  
  
 从客户端的角度来看，审批过程的工作方式如下：  
  
1.  客户端申请成为审批过程系统中的用户。  
  
2.  WCF 客户端将发送到审批管理器应用程序承载的 WCF 服务。  
  
3.  将唯一的用户 ID 返回到客户端。 此时，客户端可参与审批过程。  
  
4.  客户端在加入后可发送文档以通过个人审批过程、团体审批过程或复合审批过程进行审批。  
  
5.  单击客户端界面中的按钮，在客户端工作流服务主机中启动工作流实例。  
  
6.  工作流将审批请求发送到审批管理器应用程序。  
  
7.  工作流管理器启动其自身的工作流以表示审批过程。  
  
8.  一旦执行管理器审批工作流，就会将结果发送回客户端。  
  
9. 客户端显示结果。  
  
10. 客户端可以随时接收审批请求并对其做出响应。  
  
11. 在客户端上承载的 WCF 服务可以从审批管理器应用程序接收审批请求。  
  
12. 客户端上将呈现文档信息以供审阅。  
  
13. 用户可以批准或拒绝文档。  
  
14. WCF 客户端用于发送回审批管理器应用程序审批响应。  
  
 从审批管理器应用程序的角度来看，审批过程的工作方式如下：  
  
1.  客户端请求加入审批过程系统。  
  
2.  审批管理器上的 WCF 服务接收的请求成为审批过程系统的一部分。  
  
3.  为客户端生成唯一的 ID。 将用户信息存储在数据库中。  
  
4.  将唯一的 ID 发送回用户。  
  
5.  接收审批请求。 审批管理器执行审批过程。  
  
6.  审批管理器接收审批请求，启动新的工作流。  
  
7.  根据请求的类型（个人、团体或复合）来执行不同的活动。  
  
8.  发送和接收相关的活动，这些活动用于向客户端发送供审阅的审批请求和从客户端接收响应。  
  
9. 将审批过程工作流的结果发送到客户端。  
  
## <a name="using-the-sample"></a>使用示例  
  
##### <a name="to-set-up-the-database"></a>安装数据库  
  
1.  使用管理员特权打开 Visual Studio 2010 命令提示符下，导航到此 DocumentApprovalProcess 文件夹并运行 Setup.cmd。  
  
##### <a name="to-set-up-the-application"></a>设置应用程序  
  
1.  使用 Visual Studio 2010 打开 DocumentApprovalProcess.sln 解决方案文件。  
  
2.  要生成解决方案，按 Ctrl+Shift+B。  
  
3.  若要运行解决方案，通过右键单击中的 ApprovalManager 项目启动审批管理器应用程序**解决方案资源管理器**，然后单击**调试**->**开始**从右键单击菜单中的新实例。  
  
     等待管理器的输出指示已做好准备工作。  
  
##### <a name="to-run-the-single-approval-scenario"></a>运行个人审批方案  
  
1.  使用管理员权限打开命令提示符。  
  
2.  导航到包含解决方案的目录。  
  
3.  导航到 ApprovalClient\Bin\Debug 文件夹并执行两个 ApprovalClient.exe 实例。  
  
4.  单击**发现**，等待，直到**订阅**按钮处于启用状态。  
  
5.  键入任何用户名，然后单击**订阅**。 对于一个客户端，使用 `UserType1` 和其他类型 `UserType2`。  
  
6.  在 `UserType1` 客户端中，从下拉菜单中选择个人审批类型，然后键入文档名称和内容。 单击**请求批准**。  
  
7.  在 `UserType2` 客户端中，将显示等待审批的文档。 选择它，然后按**批准**或**拒绝**。 结果将显示在 `UserType1` 客户端中。  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>运行团体审批方案  
  
1.  使用管理员权限打开命令提示符。  
  
2.  导航到包含解决方案的目录。  
  
3.  导航到 ApprovalClient\Bin\Debug 文件夹并执行三个 ApprovalClient.exe 实例。  
  
4.  单击**发现**，等待，直到**订阅**按钮处于启用状态。  
  
5.  键入任何用户名，然后单击**订阅**。 对于一个客户端，使用 `UserType1` 和其他两个类型 `UserType2`。  
  
6.  在 `UserType1` 客户端中，从下拉菜单中选择团体审批类型，然后键入文档名称和内容。 单击**请求批准**。 这将请求两个 `UserType2` 客户端批准或拒绝该文档。 虽然两个 `UserType2` 客户端都必须做出响应，但只需一个客户端批准文档即可使文档获得审批。  
  
7.  在 `UserType2` 客户端中，将显示等待审批的文档。 选择它，然后按**批准**或**拒绝**。 结果将显示在 `UserType1` 客户端中。  
  
##### <a name="to-run-the-complex-approval-scenario"></a>运行复合审批方案  
  
1.  使用管理员权限打开命令提示符。  
  
2.  导航到包含解决方案的目录。  
  
3.  导航到 ApprovalClient\Bin\Debug 文件夹并执行四个 ApprovalClient.exe 实例。  
  
4.  单击**发现**，等待，直到**订阅**按钮处于启用状态。  
  
5.  键入任何用户名，然后单击**订阅**。 为第一个客户端使用 `UserType1`，为第二个客户端使用 `UserType2`，为最后一个客户端使用 `UserType3`。  
  
6.  在 `UserType1` 客户端中，从下拉菜单中选择个人审批类型，然后键入文档名称和内容。 单击**请求批准**。  
  
7.  在 `UserType2` 客户端中，将显示等待审批的文档。 选择它，然后按**批准**，该文档传递到`UserType3`客户端。  
  
     如果第一个 `UserType2` 团体批准该文档，则该文档将传递到 `UserType3` 客户端。  
  
8.  批准或拒绝来自 `UserType3` 客户端的文档。 结果将显示在 `UserType1` 客户端中。  
  
##### <a name="to-clean-up"></a>清理  
  
1.  从 Visual Studio 2010 命令提示符，导航到 DocumentApprovalProcess 文件夹并运行 Cleanup.cmd。
