---
title: 教程：定义 Windows Communication Foundation 服务协定
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: f93ef787c74a4581d45c24c5a704cc5fb044bd46
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409960"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>教程：定义 Windows Communication Foundation 服务协定

本教程介绍创建基本 Windows Communication Foundation (WCF) 应用程序所需的五个任务的第一个。 有关教程的概述，请参阅[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。

创建 WCF 服务时，您的首要任务是定义服务协定。 服务协定指定服务支持的操作。 可以将操作视为一个 Web 服务方法。 通过定义视觉对象创建服务协定C#或 Visual Basic (VB) 接口。 接口具有以下特征：

- 接口中的每个方法都对应于特定的服务操作。 
- 对于每个接口，你必须应用<xref:System.ServiceModel.ServiceContractAttribute>属性。
- 对于每个操作/方法，你必须应用<xref:System.ServiceModel.OperationContractAttribute>属性。 

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建**WCF 服务库**项目。
> - 定义服务协定接口。


## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>创建 WCF 服务库项目并定义服务协定接口

1. 以管理员身份打开 Visual Studio。 若要执行此操作，请选择中的 Visual Studio 程序**启动**菜单，并选择**详细** > **以管理员身份运行**从快捷菜单。

2. 创建**WCF 服务库**项目。

   1. 从“文件”菜单中选择“新建” > “项目”。

   2. 在中**新的项目**对话框中的，在左侧，展开**Visual C#** 或**Visual Basic**，然后选择**WCF**类别。 Visual Studio 窗口的中心部分中显示项目模板的列表。 选择**WCF 服务库**。

      > [!NOTE]
      > 如果没有看到**WCF**项目模板类别中，您可能需要安装**Windows Communication Foundation**组件的 Visual Studio。 在中**新的项目**对话框中，选择**打开 Visual Studio 安装程序**左侧和右侧的链接。 选择**各个组件**选项卡，然后找到并选择**Windows Communication Foundation**下**开发活动**类别。 选择**修改**以开始安装该组件。

   3. 在窗口的下半部分中，输入*GettingStartedLib*有关**名称**并*GettingStarted*有关**解决方案名称**。 

   4. 选择 **确定**。

      Visual Studio 创建项目，它具有三个文件：*IService1.cs* (或*IService1.vb* Visual Basic 项目)， *Service1.cs* (或*Service1.vb* Visual Basic 项目)，和*App.config*。Visual Studio 定义这些文件，如下所示： 
      - *IService1*文件包含服务协定的默认定义。 
      - *Service1*文件包含服务协定的默认实现。 
      - *App.config*文件包含加载具有 Visual Studio WCF 服务主机工具的默认服务所需的配置信息。 有关 WCF 服务主机工具的详细信息，请参阅[WCF 服务主机 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)。

      > [!NOTE]
      > 如果使用 Visual Basic 开发人员环境设置安装 Visual Studio，解决方案可能被隐藏。 如果这种情况，请选择**选项**从**工具**菜单中，然后选择**项目和解决方案** > **常规**中**选项**窗口。 选择**总是显示解决方案**。 此外，检查是否**保存新项目时创建**处于选中状态。


3. 从**解决方案资源管理器**，打开**IService1.cs**或**IService1.vb**文件，并其代码替换为以下代码：

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     本协定定义了一个在线计算器。 请注意`ICalculator`接口将标有<xref:System.ServiceModel.ServiceContractAttribute>属性 (为简化`ServiceContract`)。 此属性定义一个命名空间以消除协定名称的歧义。 该代码将标记与每个计算器操作<xref:System.ServiceModel.OperationContractAttribute>属性 (为简化`OperationContract`)。

## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建 WCF 服务库项目。
> - 定义服务协定接口。

转到下一步的教程，了解如何实现 WCF 服务约定。

> [!div class="nextstepaction"]
> [教程：实现 WCF 服务约定](how-to-implement-a-wcf-contract.md)
