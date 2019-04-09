---
title: 将 .NET 远程处理应用程序迁移到 WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091106"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>将 .NET 远程处理应用程序迁移到 WCF
**本主题介绍一项传统技术，保留该技术是为了向后兼容现有的应用程序，不建议对新的开发使用该技术。 现在应使用 WCF 开发分布式应用程序。**  
  
 有两种方法来利用现有的.NET 远程处理应用程序的 WCF： 集成和迁移。 集成，可有.NET Remoting 2.0 和 WCF 并行运行，让你无需修改现有的.NET Remoting 2.0 代码同时通过这两种技术公开相同的业务对象。 集成要求运行 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 或更高版本。 如果你想要利用 WCF 功能，并且不需要与 Remoting 2.0 系统的网络兼容性，可以将整个服务迁移到 WCF。 从.NET Remoting 2.0 迁移到 WCF 要求对远程对象的接口和其配置设置的更改。 这两个主题中介绍[从远程处理与 Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403)。  
  
## <a name="see-also"></a>请参阅

- [概念概述](../../../../docs/framework/wcf/conceptual-overview.md)
