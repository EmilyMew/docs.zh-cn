---
title: 如何：获取证书 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 03ee861f7eba8b2ecee6b4697c5b475eacf78c89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093899"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>如何：获取证书 (WCF)
若要使用任何 Windows Communication Foundation (WCF) 的功能，使用 X.509 证书，必须先获取证书。  
  
### <a name="to-obtain-an-x509-certificate"></a>获取 X.509 证书  
  
1.  选择以下选项之一：  
  
    -   从证书颁发机构（如 VeriSign Inc）购买证书。  
  
    -   设置自己的证书服务，并让证书颁发机构为证书签名。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]Windows 2000 Server、 Windows 2000 Server Datacenter 和 Windows 2000 Datacenter Server 所有包括支持公钥基础结构 (PKI) 证书服务。 在 Windows Server 2008 中，使用[Active Directory 证书服务](https://go.microsoft.com/fwlink/?LinkID=153483)角色来管理证书颁发机构。  
  
    -   设置自己的证书服务，但不对证书进行签名。  
  
    > [!NOTE]
    >  无论采取哪种方法，包含 X.509 证书的 SOAP 请求的接收方都必须信任 X.509 证书。 这意味着证书链中的 X.509 证书或颁发者位于“受信任的人”证书存储区中，并且 X.509 证书不在“不受信任的证书”存储区中。  
  
## <a name="see-also"></a>请参阅

- [使用证书](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [如何：创建开发期间使用的临时证书](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
