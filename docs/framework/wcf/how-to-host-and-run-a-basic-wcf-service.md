---
title: 教程：托管并运行基本的 Windows Communication Foundation 服务
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 38fd9b89e2719be8ce4d33b1b50f68171d587369
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410090"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>教程：托管并运行基本的 Windows Communication Foundation 服务

本教程介绍创建基本 Windows Communication Foundation (WCF) 应用程序所需的五个任务的第三个。 有关教程的概述，请参阅[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。

下一个任务创建的 WCF 应用程序是托管在一个控制台应用程序中的 WCF 服务。 WCF 服务公开一个或多个*终结点*，其中每个都公开一个或多个服务操作。 服务终结点指定以下信息： 
- 在哪里可以找到该服务的地址。
- 一个绑定，它包含描述如何在客户端必须与服务通信的信息。 
- 定义服务向其客户端提供的功能的协定。

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建和配置用于承载 WCF 服务的控制台应用项目。
> - 添加代码以承载 WCF 服务。
> - 更新配置文件。
> - 启动 WCF 服务并验证其是否正在运行。


## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>创建和配置托管服务的一个控制台应用程序项目

1. 在 Visual Studio 中创建一个控制台应用程序项目： 
 
    1. 从**文件**菜单中，选择**打开** > **项目/解决方案**并浏览到**GettingStarted**解决方案，以前创建的 (*GettingStarted.sln*)。 选择“打开” 。

    2. 从**视图**菜单中，选择**解决方案资源管理器**。
    
    3. 在中**解决方案资源管理器**窗口中，选择**GettingStarted**解决方案 （高层节点），然后选择**添加** > **的新项目**从快捷菜单。 

    4. 在中**添加新项目**窗口中的，左侧和右侧，选择**Windows Desktop**类别中的下**Visual C#** 或**Visual Basic**. 

    5. 选择**控制台应用 (.NET Framework)** 模板，并输入*GettingStartedHost*有关**名称**。 选择 **确定**。

2. 添加引用**GettingStartedHost**投影到**GettingStartedLib**项目： 

    1. 在中**解决方案资源管理器**窗口中，选择**引用**下的文件夹**GettingStartedHost**项目，，然后选择**添加引用**从快捷菜单。 

    2. 在中**添加引用**对话框下**项目**在窗口的左侧，选择**解决方案**。 
 
    3. 选择**GettingStartedLib**中的窗口中，并选择中心部分**确定**。 

       此操作使得中定义的类型**GettingStartedLib**项目可供**GettingStartedHost**项目。

3. 添加引用**GettingStartedHost**投影到<xref:System.ServiceModel>程序集： 

    1. 在中**解决方案资源管理器**窗口中，选择**引用**下的文件夹**GettingStartedHost**项目，，然后选择**添加引用**从快捷菜单。
    
    2. 在中**添加引用**窗口下**程序集**在窗口的左侧，选择**Framework**。 

    3. 选择**System.ServiceModel**，然后选择**确定**。 
    
    4. 通过选择保存解决方案**文件** > **全部保存**。

## <a name="add-code-to-host-the-service"></a>添加代码以承载服务

若要托管该服务，你可以添加代码以执行以下步骤： 
   1. 创建的基址 URI。
   2. 创建用于承载服务的类实例。
   3. 创建服务终结点。
   4. 启用元数据交换。
   5. 打开服务主机以侦听传入消息。
  
对代码进行以下更改：

1. 打开**Program.cs**或**Module1.vb**文件中**GettingStartedHost**项目，其代码替换为以下代码：

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    有关此代码的工作方式的信息，请参阅[服务托管计划步骤](#service-hosting-program-steps)。


2. 更新项目属性：

   1. 在中**解决方案资源管理器**窗口中，选择**GettingStartedHost**文件夹，，然后选择**属性**从快捷菜单。

   2. 上**GettingStartedHost**属性页上，选择**应用程序**选项卡：

      - 有关C#项目中，选择**GettingStartedHost.Program**从**启动对象**列表。

      - 对于 Visual Basic 项目中，选择**Service.Program**从**启动对象**列表。

   3. 从**文件**菜单中，选择**全部保存**。


## <a name="verify-the-service-is-working"></a>验证服务正常工作

1. 构建解决方案，然后运行**GettingStartedHost**控制台应用程序从 Visual Studio 内部。 

    必须使用管理员特权运行服务。 因为在运行时使用管理员特权打开 Visual Studio **GettingStartedHost**在 Visual Studio 中，应用程序运行使用管理员的权限。 或者，可以打开新的命令提示符以管理员身份 (选择**更多** > **以管理员身份运行**从快捷菜单) 并运行**GettingStartedHost.exe**其内。

2. 打开 web 浏览器并浏览到服务的页面在`http://localhost:8000/GettingStarted/CalculatorService`。
   
   > [!NOTE]
   > 此类服务需要适当的权限来为要侦听的计算机上注册 HTTP 地址。 管理员帐户具有此权限，但对于非管理员帐户来说，必须授予对 HTTP 命名空间的权限。 有关如何配置命名空间预留的详细信息，请参阅[配置 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。 


## <a name="service-hosting-program-steps"></a>服务宿主程序步骤

添加到主机服务进行了介绍，如下所示的代码中的步骤：

- **步骤 1**:创建的实例`Uri`类来保存服务的基址。 包含一个基址的 URL 采用一个可选 URI，这标识服务。 基址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。 计算器服务的基址使用 HTTP 传输协议、 本地主机、 端口 8000 和 URI 段，GettingStarted。

- **步骤 2**:创建的实例<xref:System.ServiceModel.ServiceHost>类，该类用于承载服务。 构造函数采用两个参数： 实现服务协定和服务的基址的类的类型。

- **步骤 3**:创建一个 <xref:System.ServiceModel.Description.ServiceEndpoint> 实例。 服务终结点由地址、绑定和服务协定组成。 <xref:System.ServiceModel.Description.ServiceEndpoint>构造函数组成的服务协定接口类型、 绑定和地址。 服务协定是在服务类型中定义和实现的 `ICalculator`。 为此示例绑定是<xref:System.ServiceModel.WSHttpBinding>，这是一个内置的绑定和连接到终结点符合 WS-* 规范。 有关 WCF 绑定的详细信息，请参阅[WCF 绑定概述](bindings-overview.md)。 将追加到基址以标识终结点的地址。 该代码指定的地址作为 CalculatorService 和作为终结点的完全限定的地址`http://localhost:8000/GettingStarted/CalculatorService`。

    > [!IMPORTANT]
    > 针对.NET Framework 版本 4 及更高版本，添加服务终结点是可选的。 对于这些版本，如果您没有添加您的代码或配置中，WCF 将添加一个默认终结点的基址和协定，该服务实现的每个组合。 有关默认终结点的详细信息，请参阅[指定的终结点地址](specifying-an-endpoint-address.md)。 有关默认终结点、 绑定和行为的详细信息，请参阅[简化后的配置](simplified-configuration.md)并[WCF 服务的简化配置](samples/simplified-configuration-for-wcf-services.md)。

- **步骤 4**:启用元数据交换。 客户端使用元数据交换来调用服务操作的生成代理。 若要启用元数据交换，创建<xref:System.ServiceModel.Description.ServiceMetadataBehavior>实例，设置其<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>属性设置为`true`，并添加`ServiceMetadataBehavior`对象传递给<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>系列<xref:System.ServiceModel.ServiceHost>实例。

- **步骤 5**:打开<xref:System.ServiceModel.ServiceHost>侦听传入消息。 应用程序等待用户按**Enter**。 应用程序实例化后<xref:System.ServiceModel.ServiceHost>，它将执行 try/catch 块。 有关安全捕获引发的异常详细信息<xref:System.ServiceModel.ServiceHost>，请参阅[使用关闭和中止发布 WCF 客户端资源](samples/use-close-abort-release-wcf-client-resources.md)。

> [!IMPORTANT]
> 当添加 WCF 服务库时，Visual Studio 承载它为您如果调试通过启动服务主机。 若要避免冲突，您可防止 Visual Studio 承载 WCF 服务库。 
> 1. 选择**GettingStartedLib**项目中**解决方案资源管理器**，然后选择**属性**从快捷菜单。
> 2. 选择**WCF 选项**并取消选中**启动 WCF 服务主机在调试同一解决方案中的另一个项目时**。


## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建和配置用于承载 WCF 服务的控制台应用项目。
> - 添加代码以承载 WCF 服务。
> - 更新配置文件。
> - 启动 WCF 服务并验证其是否正在运行。

转到下一步的教程，了解如何创建 WCF 客户端。

> [!div class="nextstepaction"]
> [教程：创建 WCF 客户端](how-to-create-a-wcf-client.md)
