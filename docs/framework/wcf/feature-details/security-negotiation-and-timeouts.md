---
title: 安全协商和超时
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180632"
---
# <a name="security-negotiation-and-timeouts"></a>安全协商和超时
当客户端和服务进行身份验证时，Windows Communication Foundation (WCF) 支持，对服务凭据协商身份验证的一部分的模式。 在这种情况下，客户端和服务之间将进行潜在多路交换，以便将服务凭据传播到客户端。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 属性控制多路交换需要多长时间才能完成。 但此超时仅在交换实际经过的时间超过单个请求响应的时间时才适用。 如果协商在一次往返中完成，则该超时不适用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [如何：设置最大时钟偏差](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
