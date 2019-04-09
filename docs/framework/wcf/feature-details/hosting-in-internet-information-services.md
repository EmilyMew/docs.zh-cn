---
title: 在 Internet 信息服务中承载
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 9cb67a30ca5453142f906be918b891ac959cdaf2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180007"
---
# <a name="hosting-in-internet-information-services"></a>在 Internet 信息服务中承载
用于承载 Windows Communication Foundation (WCF) 服务的一个选项是 Internet 信息服务 (IIS) 应用程序内。 此承载模型与 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 ASP.NET Web 服务 (ASMX) 使用的模型类似。  
  
## <a name="versions-of-iis"></a>IIS 的版本  
 可以在以下操作系统上的以下版本的 IIS 上承载 WCF:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上的 IIS 5.1。 此环境对于设计和开发 IIS 承载的应用程序非常有用，这些应用程序稍后将部署在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 等服务器操作系统上。  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 在[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]。 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 提供了一个高级的过程模型，提供改进的可伸缩性、 可靠性和应用程序隔离。 此环境适合以独占方式使用 HTTP 通信的 WCF 服务的生产部署。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 和 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上的 IIS 7.0。 IIS 7.0 提供了与 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 相同的高级进程模型，但它使用 Windows 进程激活服务 (WAS) 来允许通过 HTTP 之外的协议进行激活和网络通信。 此环境适合于通过任何支持的 WCF （包括 HTTP、 net.tcp、 net.pipe 和 net.msmq） 的网络协议进行通信的 WCF 服务的开发。 有关 WAS 的详细信息，请参阅[在 Windows 进程激活服务中承载](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。  
  
-   [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496)适用于[!INCLUDE[iisver](../../../../includes/iisver-md.md)]和 Windows 进程激活服务 (WAS) 提供丰富的应用程序宿主环境为 NET4 WCF 和 WF 服务。 这些优点包括进程生命周期管理、进程回收、共享承载、快速失败保护、进程孤立、按需激活和运行状况监视。 有关详细信息，请参阅[AppFabric 承载功能](https://go.microsoft.com/fwlink/?LinkId=196494)并[AppFabric 承载概念](https://go.microsoft.com/fwlink/?LinkId=196495)。  
  
## <a name="benefits-of-iis-hosting"></a>IIS 承载的好处  
 承载在 IIS 中的 WCF 服务有以下优点：  
  
-   在 IIS 中承载的 WCF 服务部署和管理任何其他类型的 IIS 应用程序，如包括[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]应用程序和 ASMX。  
  
-   IIS 提供进程激活、运行状况管理和回收功能以提高承载的应用程序的可靠性。  
  
-   像[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]，WCF 服务承载于[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]可以充分利用[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]提高的服务器密度和可伸缩性的常见辅助进程中的多个应用程序所在的共享宿主模型。  
  
-   在 IIS 中承载的 WCF 服务使用相同的动态编译模型[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]，从而简化了开发和部署的托管服务。  
  
 在决定在 IIS 中承载 WCF 服务时，务必要记住 IIS 5.1 和[!INCLUDE[iis601](../../../../includes/iis601-md.md)]限制为仅使用 HTTP 通信。 有关选择宿主环境的详细信息，请参阅[托管服务](../../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>部署 IIS 承载的 WCF 服务  
 开发和部署 IIS 承载的 WCF 服务包含以下任务：  
  
-   请确保，IIS、 ASP.NET、 WCF 和 WCF HTTP 激活组件正确安装和注册。  
  
-   创建新的 IIS 应用程序，或重新使用现有的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 应用程序。  
  
-   创建 WCF 服务的.svc 文件。  
  
-   将服务实现部署到 IIS 应用程序。  
  
-   配置 WCF 服务。  
  
 每个任务的讨论，请参阅[部署服务承载的 WCF 服务](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)。  
  
## <a name="wcf-services-and-aspnet"></a>WCF 服务和 ASP.NET  
 WCF 服务可以是托管任一--与并行[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]或在[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]中的服务可以充分利用提供的功能的兼容性模式[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 应用程序平台。 有关这些功能的讨论，请参阅[WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。  
  
## <a name="see-also"></a>请参阅

- [使用 ServiceHostFactory 扩展宿主](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [部署承载于 Internet 信息服务中的 WCF 服务](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Internet 信息服务承载最佳实践](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [为 Windows Communication Foundation 配置 Internet Information Services 7.0](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Windows Server App Fabric 承载功能](https://go.microsoft.com/fwlink/?LinkId=201276)
