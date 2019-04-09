---
title: WCF 所要求的操作系统资源
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100925"
---
# <a name="operating-system-resources-required-by-wcf"></a>WCF 所要求的操作系统资源
Windows Communication Foundation (WCF) 取决于提供的函数将操作系统的多个资源。 下表列出了这些资源。  
  
|资源|描述|  
|--------------|-----------------|  
|Microsoft 分布式事务协调器 (MSDTC)|支持 OleTx 事务所必需。|  
|Internet 信息服务 (IIS)|如果希望使用 IIS 来承载应用程序，则是必需的。|  
|Windows 进程激活服务 (WAS)|如果希望使用 WAS 来承载应用程序，则是必需的。|  
  
## <a name="see-also"></a>请参阅

- [系统要求](../../../docs/framework/wcf/wcf-system-requirements.md)
