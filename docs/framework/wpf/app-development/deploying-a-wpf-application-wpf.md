---
title: 部署 WPF 应用程序 (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 35515d37756c46d7d38ca272d76da3126fde385f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132349"
---
# <a name="deploying-a-wpf-application-wpf"></a>部署 WPF 应用程序 (WPF)
Windows Presentation Foundation (WPF) 应用程序构建后，它们需要部署。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和.NET Framework 包括多项部署技术。 用于部署 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序的部署技术取决于应用程序的类型。 本主题将简要概述各项部署技术，以及如何使用这些技术来满足各类 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序的部署要求。  

<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>部署技术  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和.NET Framework 包括多项部署技术，包括：  
  
-   XCopy 部署。  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署。  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 部署。  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy 部署  
 XCopy 部署是指使用 XCopy 命令行程序将文件从一个位置复制到另一个位置。 XCopy 部署适用于下列情况：  
  
-   应用程序是自包含的。 无需更新客户端，即可运行。  
  
-   应用程序文件必须从一个位置移到另一个位置，如从生成位置（本地磁盘、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 文件共享等）移到发布位置（网站、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] 文件共享等）。  
  
-   应用程序无需进行 Shell 集成（“开始”菜单快捷方式、桌面图标等）。  
  
 XCopy 适用于简单的部署方案；如果需要更为复杂的部署功能，则会限制使用 XCopy。 具体而言就是，使用 XCopy 往往会导致创建、执行并维护能以可靠方式管理部署的脚本，并进而产生相应的开销。 此外，XCopy 不支持版本控制、卸载或回滚。  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows Installer  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 允许应用程序打包为独立的可执行文件，可轻松地分发到客户端和运行。 此外，[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 会随 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 一起安装，并能与桌面、“开始”菜单及“程序”控制面板集成。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 简化了安装和卸载的应用程序，但它不提供相应工具以确保已安装应用程序保持最新版本。  
  
 有关 Windows Installer 的详细信息，请参阅[Windows Installer 部署](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)。
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 使非 Web 应用程序的 Web 样式应用程序部署。 应用程序会发布到 Web 或文件服务器，也会从 Web 或文件服务器进行部署。 尽管 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 不支持 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 安装的应用程序所支持的所有客户端功能，但它支持其中的部分功能，包括：  
  
-   与“开始”菜单及“程序”控制面板集成。  
  
-   版本控制、回滚和卸载。  
  
-   联机安装模式，该模式始终会从部署位置启动应用程序。  
  
-   当有新版本发布时自动更新。  
  
-   注册文件扩展名。  
  
 有关 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 的详细信息，请参阅 [ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)。  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>部署 WPF 应用程序  
 适用于 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序的部署选项取决于应用程序的类型。 从部署的角度来看，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 共有三种重要的应用程序类型：  
  
-   独立应用程序。  
  
-   仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 应用程序。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>部署独立应用程序  
 独立应用程序使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 或 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 来部署。 无论使用哪一项，独立应用程序都要在完全信任的状态下才能运行。 使用 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 部署的独立应用程序会被自动授予完全信任状态。 使用 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 部署的独立应用程序不会被自动授予完全信任状态。 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 会转而显示安全警告对话框，用户必须先执行接受操作，然后独立应用程序才会安装。 如果接受，独立应用程序就会安装并被授予完全信任状态。 如果不接受，则独立应用程序不会安装。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>部署仅标记 XAML 应用程序  
 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面通常会发布到 Web 服务器（如 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 页面），并可以使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 来查看。 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面会按照 Internet 区域权限集定义的限制，在部分信任的安全沙箱内运行。 这样即可提供一个与基于 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 的 Web 应用程序一样安全的沙箱。  
  
 有关 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序安全性的详细信息，请参阅[安全性](../security-wpf.md)。  
  
 仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面可以利用 XCopy 或 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] 安装到本地文件系统。 可以使用查看这些页面[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]或 Windows 资源管理器。  
  
 有关 XAML 的详细信息，请参阅 [XAML 概述 (WPF)](../advanced/xaml-overview-wpf.md)。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>部署 XAML 浏览器应用程序  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 是已编译的应用程序需要以下要部署的三个文件：  
  
-   *ApplicationName*.exe:可执行程序集应用程序文件。  
  
-   *ApplicationName*.xbap:部署清单。  
  
-   *ApplicationName*.exe.manifest 的清单：应用程序清单。  
  
> [!NOTE]
>  有关部署和应用程序清单的详细信息，请参阅[生成 WPF 应用程序](building-a-wpf-application-wpf.md)。  
  
 这些文件在 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 生成时产生。 有关详细信息，请参阅[如何：创建新的 WPF 浏览器应用程序项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100))。 和仅标记 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 页面一样，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 通常会发布到 Web 服务器并使用 [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] 来查看。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可以将部署到客户端使用任意部署技术。 但是，建议使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]，因为它提供以下功能：  
  
1.  当有新版本发布时自动更新。  
  
2.  适用于在完全信任状态下运行的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的提升权限。  
  
 默认情况下，ClickOnce 会使用.deploy 扩展名来发布应用程序文件。 这可能会引发问题，但可被禁用。 有关详细信息，请参阅 [ClickOnce 部署中的服务器和客户端配置问题](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)。  
  
 有关部署 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的详细信息，请参阅 [WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>安装 .NET Framework  
 若要运行[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]应用程序，必须在客户端上安装 Microsoft.NET Framework。 [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] 使用.NET Framework 是否安装了客户端将自动检测时[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]查看浏览器承载的应用程序。 如果未安装.NET Framework，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]会提示用户安装它。  
  
 若要检测是否安装了.NET Framework，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]包括一个引导程序应用程序注册为回退[!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)]具有以下扩展名的内容文件的处理程序：.xaml、.xps、.xbap 和.application。 如果你导航到这些文件类型，并且在客户端上未安装.NET Framework，引导程序应用程序请求权限以完成安装。 如果未提供权限，.NET Framework 和应用程序都不会安装。  
  
 如果授予权限，[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]下载并安装.NET Framework 使用[!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)]。 安装成功后的.NET framework，最初请求的文件是在新的浏览器窗口中打开。  
  
 .NET framework 自动检测已接入[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]， [!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)]，并[!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)]具有的客户端[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]或更高版本。  
  
 有关详细信息，请参阅[部署 .NET Framework 和应用程序](../../deployment/index.md)。  
  
## <a name="see-also"></a>请参阅

- [生成 WPF 应用程序](building-a-wpf-application-wpf.md)
- [安全性](../security-wpf.md)
