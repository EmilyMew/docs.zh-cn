---
title: WCF 测试客户端 (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: cd6f0d7a98ca5bc5f6bee45ad296341a5b91b2a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106764"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF 测试客户端 (WcfTestClient.exe)
Windows Communication Foundation (WCF) 测试客户端 (WcfTestClient.exe) 是一个 GUI 工具，使用户能够输入测试参数、 将该输入到服务，提交并查看服务发回的响应。 它提供了完美的服务测试体验与 WCF 服务主机结合使用时。  
  
 通常可以在以下位置找到 WCF 测试客户端 (WcfTestClient.exe): `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -社区可能是其中一个"企业"，"Professional"或"Community"具体取决于哪一级别的 Visual Studio 安装。
  
## <a name="scenarios-for-using-test-client"></a>使用测试客户端的方案  
 以下各节讨论在其中您可以使用 WCF 测试客户端来简化开发过程的最常见方案。  
  
### <a name="inside-visual-studio"></a>Visual Studio 内部  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF 服务主机启动 WCF 测试客户端和一项服务  
 创建新的 WCF 服务项目并按 F5 启动调试器后，WCF 服务主机开始将服务托管在你的项目。 然后，WCF 测试客户端打开并显示配置文件中定义的服务终结点的列表。 可以测试参数和调用服务，并可以重复此过程以继续测试和验证服务。  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF 服务主机启动 WCF 测试客户端和多项服务  
 WCF 测试客户端还可用于帮助调试包含多个服务的服务项目。 WCF 测试客户端打开后，它自动循环访问你的项目中的服务列表并将其打开进行测试。  
  
### <a name="outside-visual-studio"></a>Visual Studio 外部  
 Visual Studio 来测试在 Internet 上的任意服务外，还可以调用 WCF 测试客户端 (WcfTestClient.exe)。 若要找到此工具，请转到以下位置：  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` （社区可以是"企业"、"Professional"或"社区"，具体取决于在计算机安装的 Visual Studio 级别之一）
  
 若要使用该工具，可以双击此文件名从该位置打开它，也可以从命令行启动它。  
  
 WCF 测试客户端将任意数目的 Uri 作为命令行参数。  这些 URI 是可以测试的服务的 URI。  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 WCF 测试客户端窗口打开后，单击**文件**->**添加服务**，并输入你想要打开的服务的终结点地址。  
  
## <a name="wcf-test-client-user-interface"></a>WCF 测试客户端用户界面  
 与单个服务或多个服务，可以使用 WCF 测试客户端。  
  
### <a name="service-operations"></a>服务操作  
 WCF 测试客户端主窗口的左的窗格列出了所有可用服务，以及它们各自的终结点和操作。  
  
 双击某个操作后，可以在具有此操作名称的新选项卡内的右窗格中查看其内容。  
  
 左窗格还列出了客户端配置文件。 双击任何项可以在新选项卡式窗口内的右窗格中显示文件的内容。  
  
### <a name="entering-test-parameters"></a>输入测试参数  
 若要查看测试参数，请双击某个操作以在右侧窗格中打开它。 参数显示在**格式化**视图默认情况下的，可以输入任意值以测试服务的参数。  
  
 若要查看消息的 XML，请单击**XML**。 若要将其发送到服务，请单击**Invoke**。  
  
 数据集参数，请单击 **...** 按钮旁边**编辑...** 若要在新窗口中显示数据网格中编辑它。 请注意的外观**复制数据集**并**粘贴数据集**按钮。 如果第一次编辑时 DataSet 对象的架构未知，则 DataGrid 为空。 您必须将具有相同架构的 DataSet 对象粘贴到 DataGrid 中的当前对象。 （请注意，在粘贴操作之前需要从其他位置复制架构。）此外可以通过单击复制 Dataset 对象以供将来使用情况**复制数据集**按钮。  
  
 服务响应将出现在测试参数下面。  
  
> [!NOTE]
>  如果预期的返回值是字符串，则结果将显示为带引号的字符串，即使提供的输入未包含在引号中，也是如此。  
  
 如果在创建服务约定时将特定操作指定为单向操作，则不会显示服务响应。 消息一旦处于排队等待发送状态，则会弹出一个对话框，通知您已成功发送消息。  
  
### <a name="session-support"></a>会话支持  
 **启动新的代理**服务操作的选项卡中的复选框可用于切换会话支持。 默认情况下清除此框。  
  
 当为某个特定操作 （或同一服务终结点中的另一个操作） 中输入测试参数并单击**Invoke**多次清除此复选框，这些操作将共用一个代理，并且服务状态为保留多个操作。  
  
 如果**启动新的代理**复选框后，新的代理启动每个**Invoke**、 上一个会话方案终止，并且会重置服务状态。  
  
### <a name="editing-client-configuration"></a>编辑客户端配置  
 WCF 测试客户端主窗口的左的窗格列出了客户端配置文件。 双击任何项可以在右窗格中显示文件的内容。  
  
#### <a name="edit-with-service-configuration-editor"></a>使用服务配置编辑器进行编辑  
 右键单击**配置文件**在左窗格中，选择上下文菜单**用 svcconfigeditor 进行编辑**。 服务配置编辑器启动并显示客户端配置内容。 可以编辑配置，然后将其保存在此工具中。  
  
 在服务配置编辑器中保存该文件之后, WCF 测试客户端显示一条警告消息，告知你该文件已外被修改，并询问是否想要重新加载它。  
  
 如果选择**是**，"Client.dll.config"选项卡中的配置内容将反映在编辑器中所做的更改。  
  
 如果选择**否**，"Client.dll.config"选项卡中的配置内容保持不变，并且修改后的内容自动保存到源文件。  
  
#### <a name="restore-to-default-configuration"></a>还原到默认配置  
 如果你想要取消所有更改并还原到默认客户端配置中，右键单击**配置文件**在左窗格中，选择上下文菜单**还原到默认配置**。加载默认配置值和还原"Client.dll.config"选项卡中的内容。  
  
#### <a name="validate-changes"></a>验证更改  
 WCF 测试客户端中正在加载已保存的更改，配置被检查针对 WCF 架构有效性。 如果发现错误，将显示一个对话框来给出错误详细信息。  
  
 在代理生成、 二进制编译或服务调用，支持编辑 （即，"编辑..."、"还原..."等） 的菜单项被禁用。 加载更新到 WCF 测试客户端配置时，将同时禁用服务调用。  
  
#### <a name="persist-client-configuration"></a>使客户端配置保持不变  
 **工具**->**选项**->**客户端配置**选项卡包含**始终重新生成配置时启动服务**选项，默认情况下启用。 此选项指定每次 WCF 测试客户端加载服务时，它重新生成基于最新的服务协定和服务 App.config 文件配置文件。  
  
 如果已编辑的客户端配置为 WCF 服务并想要始终使用此更新后的文件来调试你的服务，可以取消选中**重新生成**选项。 通过此操作，即使更新服务并重新打开 WCF 测试客户端，Client.dll.config 文件将是你先前更新而不是重新生成一个基于更新的服务的一个。  
  
 但是，您可能需要编辑此配置文件以使其与重新生成的代理一致。 如果由于更新了服务而导致重新生成的代理与配置文件不匹配，则调用该服务时将出错。  
  
> [!CAUTION]
>  如果您已修改了客户端配置文件并选择以后再使用它，则可以在以下位置找到此文件：  
>   
>  \Documents 和设置\\[User Account] \My Documents\Test 客户端项目。  
>   
>  任何存储到客户端配置文件的已更新的凭据信息都是由此文件夹的访问控制列表 (ACL) 保护的。  
  
### <a name="adding-removing-and-refreshing-services"></a>添加、删除和刷新服务  
  
#### <a name="add-service"></a>添加服务  
 单击**文件**->**添加服务**将服务添加到 WCF 测试客户端。 然后您需要键入要添加的服务的 URI（终结点地址）。 该服务的地址可以是 mex 地址，也可以是 WSDL 地址。  
  
 此外可以找到列表中 10 个最近添加了的服务的终结点**最新服务**子菜单。 如果选择其中之一，指定的服务添加到 WCF 测试客户端。  
  
 此外可以右击服务树的根**我的服务项目**，然后选择**添加的服务**来实现相同的结果。  
  
 在代理生成、二进制编译或服务调用期间，支持添加服务的菜单项被禁用。 服务调用也被禁用。  
  
#### <a name="remove-service"></a>移除服务  
 右键单击要删除，并且选择的服务的服务根**删除服务**从 WCF 测试客户端中删除服务。  
  
 在代理生成、二进制编译或服务调用期间，支持删除服务的菜单项被禁用。 服务调用也被禁用。  
  
#### <a name="refresh-service"></a>刷新服务  
 如果运行 WCF 测试客户端和你想要确保该服务的 WCF 测试客户端实现是最新时，将向服务进行更改，右键单击该服务，然后选择的服务根**刷新服务**。 请注意，刷新后服务状态将重置。  
  
 在代理生成、二进制编译或服务调用期间，支持刷新服务的菜单项被禁用。 服务调用也被禁用。  
  
## <a name="location-of-files-generated-by-the-test-client"></a>测试客户端生成的文件的位置  
 默认情况下，WCF 测试客户端存储在"%appdata%\Local\temp\Test Client Projects"文件夹中生成客户端代码和配置文件。 WCF 测试客户端退出后，将删除此文件夹。 如果在 WCF 测试客户端中修改配置文件和**始终重新生成启动服务时配置**选项处于禁用状态，修改后的文件复制到"My Documents\Test Client Projects"下的"CachedConfig"文件夹使用映射 （元数据的地址-到--文件名） XML 文件的索引。  
  
 你还可以在命令行中，使用启动 WCF 测试客户端`/ProjectPath`开关来指定新的所需的路径用于存储生成的文件，或者使用`/RestoreProjectPath`开关还原默认位置。 语法如下所示：  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 运行此命令不会打开 WCF 测试客户端。 而只会更改文件夹位置。 是否正在运行 WCF 测试客户端，可以运行此命令。 重新启动 WCF 测试客户端时，将应用新位置。 在注册表中，或在"%appdata%\Local\temp\Test Client Projects"文件夹的 WcfTestClient.exe.option 文件中，可以保存的位置信息。  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF 测试客户端支持的功能  
 以下是 WCF 测试客户端支持的功能的列表：  
  
-   服务调用：请求/响应和单向消息。  
  
-   绑定：Svcutil.exe 支持的所有绑定。  
  
-   控制会话。  
  
-   消息协定。  
  
-   XML 序列化。  
  
 以下是 WCF 测试客户端不支持的功能的列表：  
  
-   类型：<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口的类型（包括相关 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 特性）、<xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 类型以及 ADO.NET <xref:System.Data.DataTable> 类型。  
  
-   双工协定。  
  
-   事务。  
  
-   安全性：[!INCLUDE[infocard](../../../includes/infocard-md.md)]、证书和用户名/密码。  
  
-   绑定：WSFederationbinding、 任何上下文绑定和 Https 绑定、 WebHttpbinding （Json 响应消息支持）。  
  
## <a name="closing-wcf-test-client"></a>关闭 WCF 测试客户端  
 你可以按以下方式关闭 WCF 测试客户端：  
  
-   上**文件**菜单上，单击**退出**。 或者，在 WCF 测试客户端主窗口中，单击**关闭**。 同时这些操作还关闭 WCF 服务自动主机并停止 Visual Studio 调试过程，如果通过 Visual Studio 启动 WCF 测试客户端。  
  
-   右键单击**WCF 服务主机**在通知区域中，然后单击图标**退出。** 这会关闭 WCF 服务自动主机和 WCF 测试客户端并停止 Visual Studio 调试过程。  
  
## <a name="see-also"></a>请参阅

- [WCF 服务主机 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
