---
title: 教程：创建 Windows Communication Foundation 客户端
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 0f7f622221e6612ecdb0ea04084d81e923218a5c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634058"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>教程：创建 Windows Communication Foundation 客户端

本教程介绍创建基本 Windows Communication Foundation (WCF) 应用程序所需的五个任务的第四个。 有关教程的概述，请参阅[教程：开始使用 Windows Communication Foundation 应用程序](getting-started-tutorial.md)。

创建 WCF 应用程序的下一个任务是通过从 WCF 服务检索元数据创建客户端。 使用 Visual Studio 添加服务引用，它将从服务的 MEX 终结点获取元数据。 Visual Studio 然后为你选择的语言中的客户端代理生成托管的源代码文件。 它还会创建客户端配置文件 (*App.config*)。 此文件使客户端应用程序连接到终结点的服务。 

> [!NOTE]
> 如果从一个在 Visual Studio 类库项目调用 WCF 服务，使用**添加服务引用**功能来自动生成代理和关联的配置文件。 但是，因为在类库项目不使用此配置文件，您需要在生成的配置文件中添加设置*App.config*调用该类库的可执行文件的文件。

> [!NOTE]
> 或者，使用[ServiceModel 元数据实用工具工具](#servicemodel-metadata-utility-tool)而不是 Visual Studio 生成代理类和配置文件。

客户端应用程序使用生成的代理类与服务通信。 此过程所述[教程：使用客户端](how-to-use-a-wcf-client.md)。

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建和配置 WCF 客户端的控制台应用程序项目。
> - 添加到 WCF 服务生成代理类和配置文件的服务引用。


## <a name="create-a-windows-communication-foundation-client"></a>创建 Windows Communication Foundation 客户端

1. 在 Visual Studio 中创建一个控制台应用程序项目： 

    1. 从**文件**菜单中，选择**打开** > **项目/解决方案**并浏览到**GettingStarted**解决方案，以前创建的 (*GettingStarted.sln*)。 选择“打开” 。

    2. 从**视图**菜单中，选择**解决方案资源管理器**。

    3. 在中**解决方案资源管理器**窗口中，选择**GettingStarted**解决方案 （高层节点），然后选择**添加** > **的新项目**从快捷菜单。 
    
    4. 在中**添加新项目**窗口中的，左侧和右侧，选择**Windows Desktop**类别中的下**Visual C#** 或**Visual Basic**. 

    5. 选择**控制台应用 (.NET Framework)** 模板，并输入*GettingStartedClient*有关**名称**。 选择 **确定**。

2. 添加引用**GettingStartedClient**投影到<xref:System.ServiceModel>程序集： 

    1.  在中**解决方案资源管理器**窗口中，选择**引用**下的文件夹**GettingStartedClient**项目，，然后选择**添加引用**从快捷菜单。 

    2. 在中**添加引用**窗口下**程序集**在窗口的左侧，选择**Framework**。
    
    3. 找到并选择**System.ServiceModel**，然后选择**确定**。 

    4. 通过选择保存解决方案**文件** > **全部保存**。

3. 添加到计算器服务的服务引用：

   1. 在中**解决方案资源管理器**窗口中，选择**引用**下的文件夹**GettingStartedClient**项目，，然后选择**添加服务引用**从快捷菜单。

   2. 在中**添加服务引用**窗口中，选择**Discover**。

      CalculatorService 服务启动和 Visual Studio 将显示在**Services**框。

   3. 选择**CalculatorService**以将其展开并显示由该服务实现的服务协定。 保留默认值**Namespace** ，然后选择**确定**。

      Visual Studio 会添加新项下的**连接的服务**中的文件夹**GettingStartedClient**项目。 


### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel 元数据实用工具工具

下面的示例演示如何根据需要使用[ServiceModel 元数据实用工具工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)生成代理类文件。 此工具生成代理类文件和*App.config*文件。 以下示例演示如何生成中的代理C#和 Visual Basic 中，分别：

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>客户端配置文件

创建客户端后，Visual Studio 将创建**App.config**中的配置文件**GettingStartedClient**项目，它应类似于下面的示例：

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

下[ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md)部分中，请注意[\<终结点 >](../configure-apps/file-schema/wcf/endpoint-element.md)元素。 **&lt;终结点&gt;** 元素定义的终结点的客户端用于访问该服务，如下所示：
- 地址： `http://localhost:8000/GettingStarted/CalculatorService`。 终结点的地址。
- 服务协定： `ServiceReference1.ICalculator`。 服务协定处理 WCF 客户端和服务之间的通信。 在使用时，visual Studio 将生成此协定及其**添加服务引用**函数。 它是约定的实质上是约定的在 GettingStartedLib 项目中定义的副本。 
- 绑定： <xref:System.ServiceModel.WSHttpBinding>。 绑定指定 HTTP 作为传输协议、 可互操作安全性和其他配置详细信息。

## <a name="next-steps"></a>后续步骤

在本教程中，你将了解：
> [!div class="checklist"]
> - 创建和配置 WCF 客户端的控制台应用程序项目。
> - 添加到 WCF 服务，以生成客户端应用程序的代理类和配置文件的服务引用。

转到下一步的教程，了解如何使用生成的客户端。

> [!div class="nextstepaction"]
> [教程：使用 WCF 客户端](how-to-use-a-wcf-client.md)


