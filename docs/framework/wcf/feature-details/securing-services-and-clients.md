---
title: 保护服务和客户端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: e455c7a48e1484d5acdcc5f6cdc9098997a3ba83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120719"
---
# <a name="securing-services-and-clients"></a>保护服务和客户端的安全
在本部分中的信息重点介绍编程安全 Windows Communication Foundation (WCF) 中。 通常，这包括选择系统提供的相应绑定、设置安全元素的属性，然后设置服务行为的属性（控制检索凭据以供服务或客户端使用的方式）。 这些技术涵盖大多数情况下，大多数用户的安全要求，如中所示[常用安全方案](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 如果你的方案需要更多的功能，首先请参阅[使用自定义绑定的安全功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); 如果解决方案并不明显，请参阅[扩展安全](../../../../docs/framework/wcf/extending/extending-security.md)。 如果要创建 （或与进行互操作） 的系统使用丰富的声明，请参阅中的主题[授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [WCF 安全编程](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 用于保护消息安全的编程模型概述。  
  
 [传输安全概述](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 如何通过传输层保护消息安全概述。  
  
 [消息安全](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 总结了使用 Windows Communication Foundation (WCF) 中的消息级安全性的原因。  
  
 [安全会话](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 讨论的所需保护 WCF 会话时的注意事项。  
  
 [使用证书](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 说明使用 X.509 证书时必须完成的一些常见任务。  
  
## <a name="reference"></a>参考  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>相关章节  
 [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [扩展安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [常用安全方案](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [绑定与安全](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [使用自定义绑定的安全功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [扩展安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>请参阅

- [基本 WCF 编程](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Server App Fabric 的安全模型](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
