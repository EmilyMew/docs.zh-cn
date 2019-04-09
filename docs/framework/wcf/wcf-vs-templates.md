---
title: WCF Visual Studio 模板
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: b0cca0cd585a45b795db4d573659e0d19ecd78dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130892"
---
# <a name="wcf-visual-studio-templates"></a>WCF Visual Studio 模板
Windows Communication Foundation (WCF) Visual Studio 模板是预定义的项目和项模板可用于在 Visual Studio 中快速构建 WCF 服务和周边应用程序。  
  
## <a name="using-the-wcf-templates"></a>使用 WCF 模板  
 WCF Visual Studio 模板为服务开发提供基本的类结构。 具体地说，这些模板提供服务协定、数据协定、服务实现和配置的基本定义。 可以使用这些模板创建代码交互最少的简单服务以及更高级的服务的构造块。  
  
### <a name="wcf-service-library-project-template"></a>WCF 服务库项目模板  
 WCF 服务库项目模板将显示在新项目对话框下**Visual C# \WCF**并**Visual Basic\WCF**。  
  
 创建新项目使用时**WCF 服务**模板，将新项目会自动包括以下三个文件：  
  
-   服务协定文件（IService1.cs 或 IService1.vb）。 服务协定文件是已应用的 WCF 服务属性的接口。 此文件提供简单服务的定义以表明如何定义服务，并且包括基于参数的操作和简单的数据协定示例。 这是创建 WCF 服务项目后显示在代码编辑器中的默认文件。  
  
-   服务实现文件（Service1.cs 或 Service1.vb）。 服务实现文件实现服务协定文件中定义的协定。  
  
-   应用程序配置文件 (App.config)。 配置文件提供安全的 HTTP 绑定的 WCF 服务模型的基本元素。 它还包括一个服务终结点，并启用了元数据交换。  
  
> [!NOTE]
>  Visual Studio 配置为使用运行时将 App.config 文件识别为项目的配置文件[WCF 服务主机 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)，这是默认配置。 如果在可执行文件中承载服务库，则由于 DLL 的配置文件无效，必须将配置代码移动到可执行文件的配置文件。  
  
### <a name="wcf-service-application-template"></a>WCF 服务应用程序模板  
 WCF 服务应用程序模板将显示在新建项目对话框下**Visual C# \WCF**并**Visual Basic\WCF**。  
  
 创建新项目使用时**WCF Web 应用程序服务**模板，项目包括以下四个文件：  
  
-   服务主机文件 (service1.svc)。  
  
-   服务协定文件（IService1.cs 或 IService1.vb）。  
  
-   服务实现文件（Service1.svc.cs 或 Service1.svc.vb）。  
  
-   Web 配置文件 (Web.config)。  
  
 此模板将自动创建一个网站（该网站将要部署到虚拟目录），并在该网站中承载服务。  
  
### <a name="wcf-web-site-template"></a>WCF 网站模板  
 WCF 网站模板将显示在新建项目对话框下**Visual C# \Web Site\WCF 服务**并**Visual Basic\Web 网站 \wcf 服务**。 这将创建与 WCF 服务应用程序模板相同的文件，但按照它是 ASP.NET 网站来进行组织。 创建 App_Code 和 App_Data 文件夹。  
  
### <a name="wcf-service-item-template"></a>WCF 服务项模板  
 WCF 服务项模板是，可以快速将 WCF 服务添加到现有的 Visual Studio 项目的自定义模板。  
  
 若要使用此模板，请转到**解决方案资源管理器**窗格中，右键单击项目名称，指向**添加**，然后单击**新项**以启动**添加新项**对话框。  
  
 服务接口和实现文件放在根项目文件夹中。  
  
 该模板尝试将新服务的配置节合并到兼容类型的现有配置文件中。  
  
 如果现有项目是 Web 项目，则也会创建服务主机文件 (service1.svc)。  
  
### <a name="wcf-wf-service-project-and-item-template"></a>WCF WF 服务项目和项模板。  
 这些模板创建的 WCF 服务承载工作流服务，这是可以访问类似于 web 服务的工作流。 XAML 或命令式编程模型具有单独的模板。 通过使用模板，可以创建顺序工作流或状态机工作流。 有关这些类型的工作流的详细信息，请参阅[如何：创建工作流](../windows-workflow-foundation/how-to-create-a-workflow.md)。 有关创建工作流项目的详细信息，请参阅[创建旧版工作流项目](/visualstudio/workflow-designer/creating-legacy-workflow-projects)。  
  
 使用工作流的 XOML 类型代替基于代码的是，visual Studio 设计器时响应速度更快。 XOML 工作流是要创建的默认工作流类型。  
  
### <a name="wcf-syndication-service-library-template"></a>WCF 联合服务库模板  
 此模板可公开为 WCF 服务的 RSS 或 ATOM 格式的源。 有关详细信息，请参阅[WCF 联合](../../../docs/framework/wcf/feature-details/wcf-syndication.md)。  
  
#### <a name="changing-the-address-of-the-feed"></a>更改源的地址  
 在执行期间，联合模板使用 Internet Explorer。 右键单击您的项目时**解决方案资源管理器**在 Visual Studio 中，选择**属性**，然后选择**调试**选项卡，您可以看到的默认地址模板。 Internet Explorer 尝试在此地址打开源。  
  
 如果你更改源的地址，则必须更改中的地址**调试**选项卡。如果不这样做，Internet Explorer 将尝试在默认地址打开源，从而失败。  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>支持 AJAX 的 WCF 服务项模板  
 此模板将 AJAX 控件公开为 WCF 服务。 AJAX 控件的详细信息，请参阅[AJAX 控件文档](https://go.microsoft.com/fwlink/?LinkId=96717)。  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>启用了 Silverlight 的 WCF 服务项模板  
 该模板创建提供数据给 Silverlight 客户端或前端的 Web 服务。 模板可以添加到网站或 Web 应用程序项目，以便创建 WCF 服务，包括服务代码和支持与 Silverlight 客户端通信的配置。 然后，可以使用**添加服务引用**将服务的客户端代理添加到客户端，并在 Silverlight 客户端和启用了 Silverlight 的 WCF 服务之间交换数据。  
  
 若要访问此模板，请右键单击在网站或 Web 应用程序项目**解决方案资源管理器**，单击**添加新项**，然后单击**启用 Silverlight 的 WCF 服务**。  
  
> [!NOTE]
>  启用了 Silverlight 的 WCF 服务公开 `basicHttpBinding` 终结点，不启用任何安全设置。 因此，连接到此服务的任何客户端都可以获取有关此服务的信息。 此外，在该服务与客户端之间交换的消息也未经过签名和加密处理。 若要正确保护该终结点，应使用 ASP.NET 身份验证、HTTPS 或其他机制。  
  
## <a name="see-also"></a>请参阅

- [WCF 服务主机 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [WCF 测试客户端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
