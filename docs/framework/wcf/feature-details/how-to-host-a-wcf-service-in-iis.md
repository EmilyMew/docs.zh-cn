---
title: 如何：在 IIS 中承载 WCF 服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 8b2ebc108bf3eef60e8877e617acec782da38fa4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124548"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>如何：在 IIS 中承载 WCF 服务
本主题概述了创建 Internet 信息服务 (IIS) 中的托管的 Windows Communication Foundation (WCF) 服务所需的基本步骤。 本主题假设您熟悉 IIS 且了解如何使用 IIS 管理工具创建和管理 IIS 应用程序。 有关 IIS 的详细信息请参阅[Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449)。 WCF 服务，运行在 IIS 环境中的充分利用 IIS 功能，如进程回收、 空闲关闭、 进程运行状况监视和基于消息的激活。 此宿主选项要求正确配置 IIS，但不需要编写任何承载代码作为应用程序的一部分。 只可以将 IIS 宿主与 HTTP 传输协议一起使用。  
  
 详细了解如何为 WCF 和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]进行交互，请参阅[WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。 有关配置安全性的详细信息，请参阅[安全](../../../../docs/framework/wcf/feature-details/security.md)。  
  
 此示例中的源副本，请参阅[IIS 承载使用内联代码](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>创建由 IIS 承载的服务  
  
1.  确认 IIS 已经安装并在计算机上运行。 有关安装和配置 IIS 的详细信息请参阅[安装和配置 IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  为应用程序文件创建一个称为“IISHostedCalcService”的新文件夹，确保 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 有权访问该文件夹的内容，并使用 IIS 管理工具创建一个物理上位于此应用程序目录中的新 IIS 应用程序。 当为应用程序目录创建别名时，请使用“IISHostedCalc”。  
  
3.  在应用程序目录中创建一个名为“service.svc”的新文件。 编辑此文件添加以下@ServiceHost元素。  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  在应用程序目录中创建 App_Code 子目录。  
  
5.  在 App_Code 子目录中创建名为 Service.cs 的代码文件。  
  
6.  将下面的 using 语句添加到 Service.cs 文件的最前面。  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  将下面的命名空间声明添加到 using 语句后面。  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  定义命名空间声明中的服务协定，如下面的代码所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 在服务协定定义后实现服务协定，如下面的代码所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. 在应用程序目录中创建一个名为“Web.config”的文件，并将下面的配置代码添加到该文件中。 在运行时，WCF 基础结构使用的信息来构造客户端应用程序可以与进行通信的终结点。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     此示例显式指定配置文件中的终结点。 如果您不希望向服务添加任何终结点，则运行时为您添加默认终结点。 有关默认终结点、 绑定和行为，请参阅详细信息[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)并[WCF 服务的简化配置](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
11. 若要确保正确承载该服务，请打开 Internet Explorer 并浏览到服务的 URL 的实例： `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>示例  
 下面是 IIS 承载的计算器服务的代码的完整列表。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>请参阅

- [在 Internet 信息服务中承载](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [承载服务](../../../../docs/framework/wcf/hosting-services.md)
- [WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
- [Windows Server App Fabric 承载功能](https://go.microsoft.com/fwlink/?LinkId=201276)
