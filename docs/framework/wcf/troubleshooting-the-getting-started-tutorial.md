---
title: 排查 Get 开始使用 Windows Communication Foundation 教程
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410493"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>排查 Get 开始使用 Windows Communication Foundation 教程

本文提供解决方案的最常见的问题和按照中的步骤时可能遇到的错误[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。 
  
## <a name="common-problems"></a>常见问题

**我找不到我的硬盘驱动器上的项目文件。**

 Visual Studio 将保存在项目文件中的*C:\Users\\&lt;用户名&gt;\source\repos*。  

**找不到*App.config*生成的文件*Svcutil.exe*。**

 在 Visual Studio 中，**添加现有项**窗口将仅显示具有以下扩展名的文件默认情况下： 
- .cs 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

若要显示所有文件类型，请选择**的所有文件 (\*。\*)** 右下角的下拉列表中**添加现有项**窗口。  
  
## <a name="common-errors"></a>常见错误

### <a name="compile-the-service-application"></a>编译服务应用程序 

**错误 BC30420 GettingStartedHost.Module1 中找不到 Sub Main。**

对于 Visual Basic 应用程序不正确的入口点。 请进行以下更改：

   1. 在中**解决方案资源管理器**窗口中，选择**GettingStartedHost**文件夹，，然后选择**属性**从快捷菜单。
    a. 在中**GettingStartedHost**窗口中，对于**启动对象**，选择**Service.Program** （或特定应用程序的入口点） 从列表中。 
    b. 从主菜单中，选择**文件** > **全部保存**。

### <a name="run-the-service-application"></a>运行服务应用程序 

**HTTP 无法注册 URL http:\// +: 8000/GettingStarted/CalculatorService。进程不具有此命名空间的访问权限。** 

 为适当的访问，启动承载具有管理权限的 Windows Communication Foundation (WCF) 服务的进程：
- 对于 Visual Studio:选择在 Visual Studio 计划**启动**菜单，并选择**详细** > **以管理员身份运行**从快捷菜单。
- 控制台窗口：选择**命令提示符**中**启动**菜单，并选择**详细** > **运行以管理员身份**的快捷方式菜单。
- Windows 资源管理器：选择可执行文件，并选择**以管理员身份运行**从快捷菜单。

### <a name="compile-the-client-application"></a>编译客户端应用程序

**CalculatorClient 不包含的定义\<方法名称 > 和扩展方法\<方法名称 > 接受的第一个参数的类型找不到 CalculatorClient (是否缺少 using 指令或程序集引用？）**  

您会使用标记的那些方法`ServiceOperationAttribute`公开公开属性。 如果省略`ServiceOperationAttribute`属性中的方法从`ICalculator`接口，在编译期间收到此错误消息。  

**找不到 CalculatorClient 的类型或命名空间名称 (是否缺少 using 指令或程序集引用？)**

 如果你未添加收到此错误*generatedProxy.cs* (或*generatedProxy.vb*) 到你的客户端项目时生成与文件*Svcutil.exe*工具.  

### <a name="run-the-client-application"></a>运行客户端应用程序

**未经处理的异常：System.ServiceModel.EndpointNotFoundException:无法连接到 http:\//localhost:8000/GettingStarted/CalculatorService。TCP 错误代码 10061:由于目标机器主动拒绝，无法建立连接。**

如果而无需第一个启动该服务运行客户端应用程序，会发生此错误。 首先，运行主机应用程序以启动该服务，然后运行客户端应用程序。

### <a name="use-the-svcutilexe-tool"></a>使用 Svcutil.exe 工具
   
**Svcutil 不识别为内部或外部命令、 可操作程序或批处理文件。**

 *Svcutil.exe*必须位于系统路径。 最简单的解决方案是使用 Visual Studio 命令提示符。 从**启动**菜单中，选择**Visual Studio\<版本 >** 目录，然后选择**VS 开发人员命令提示\<版本 >**. 此命令提示符下设置为正确的位置的 Visual Studio 中附带的所有工具的系统路径。  
  
### <a name="run-the-service-and-client-applications"></a>运行服务和客户端应用程序

**System.ServiceModel.Security.SecurityNegotiationException:与 SOAP 安全协商 http:\//localhost:8000/GettingStarted/CalculatorService 目标 http:\//localhost:8000/GettingStarted/CalculatorService 失败**  

无网络连接的已加入域的计算机上出现此错误。 将计算机连接到网络或关闭服务和客户端的安全性。 

若要关闭安全性：

- 对于服务，将代码替换为创建`WSHttpBinding`使用以下代码：  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 对于客户端配置文件中更新**\<安全 >** 元素下的**\<绑定 >** 元素，如下所示：  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>请参阅  
 [开始使用 WCF 应用程序](getting-started-tutorial.md)  
 [WCF 疑难解答快速入门](wcf-troubleshooting-quickstart.md)  
 [安装问题疑难解答](troubleshooting-setup-issues.md)
