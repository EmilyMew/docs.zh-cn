---
title: 支持 .NET 应用程序部署的 Firefox 加载项
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 4b0552ab9f565d9118415bc2da2823762f34fe2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111730"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>支持 .NET 应用程序部署的 Firefox 加载项
Windows Presentation Foundation (WPF) 适用于 Firefox 和.NET Framework Assistant firefox 插件启用[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、 松散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，和 ClickOnce 应用程序以使用 Mozilla Firefox 浏览器。  
  
## <a name="wpf-plug-in-for-firefox"></a>Firefox WPF 插件  
 Firefox 的插件的 WPF 启用[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]和宽松[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要导航到并运行位于顶级或 Firefox 浏览器中 HTML IFRAME 中的文件。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]可发布到 Web 服务器和在启动应用程序支持的浏览器。 松散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是一个仅 XAML 文件，可以导航到并显示在支持的浏览器，类似于 XML 文件。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]与已安装 Firefox 插件[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 Window 7 包括[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，但不包括[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 的插件。 不能安装[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Windows 7 上的 Firefox 的插件。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不包括[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Firefox 的插件。 但是，如果两个[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]并[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]是安装，随一起安装的 WPF 插件 Firefox [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。 因此[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]应用程序仍将运行，因为 WPF 宿主将加载正确版本的 framework。 有关详细信息，请参阅[WPF 主机 (PresentationHost.exe)](wpf-host-presentationhost-exe.md)。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 .NET Framework Assistant firefox 允许独立 ClickOnce 应用程序从 Firefox 浏览器中运行。 .NET Framework Assistant Firefox 函数的相同安装之前和之后的 Firefox 浏览器。 Firefox 浏览器启动时和[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]是安装，Firefox 找到并安装了适用于 Firefox 的.NET Framework Assistant。 用户可以配置的.NET Framework Assistant firefox 来执行以下操作：  
  
-   运行 ClickOnce 应用程序之前进行提示。  
  
-   报告所有已安装的版本的.NET Framework 或只是最新版本。  
  
 .NET Framework Assistant firefox 是附带[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]。 有关删除适用于 Firefox 的.NET Framework Assistant 的信息，请参阅[如何删除适用于 Firefox 的.NET Framework Assistant](https://go.microsoft.com/fwlink/?LinkId=177944)。  
  
## <a name="see-also"></a>请参阅

- [部署 WPF 应用程序](deploying-a-wpf-application-wpf.md)
- [WPF XAML 浏览器应用程序概述](wpf-xaml-browser-applications-overview.md)
- [检测是否安装了适用于 Firefox 的 WPF 插件](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
