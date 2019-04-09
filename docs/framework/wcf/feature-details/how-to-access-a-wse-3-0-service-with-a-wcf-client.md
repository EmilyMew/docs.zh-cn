---
title: 如何：访问 WSE 3.0 服务与 WCF 客户端
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 1b8b344c713fdd27c67cf98c51c8c69198fd508f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127450"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>如何：访问 WSE 3.0 服务与 WCF 客户端
WCF 客户端配置为使用 2004 年 8 月版的 Ws-addressing 规范时，Windows Communication Foundation (WCF) 客户端是 Microsoft.NET 服务的网络级别兼容性与 Web Services Enhancements (WSE) 3.0。 但是，WSE 3.0 服务不支持元数据交换 (MEX) 协议，因此当你使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)若要创建 WCF 客户端类，安全设置不会应用到生成WCF 客户端。 因此，必须指定安全设置 WSE 3.0 服务，需要生成 WCF 客户端之后。  
  
 可以通过使用自定义绑定 WSE 3.0 服务的要求以及 WSE 3.0 服务与 WCF 客户端之间的互操作性要求，需要考虑应用这些安全设置。 这些互操作性需求包括前面提到的使用 2004 年 8 月版的 WS-Addressing 规范和 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> 的 WSE 3.0 默认消息保护。 WCF 的默认消息保护是<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>。 本主题详细介绍了如何创建与 WSE 3.0 服务互操作的 WCF 绑定。 WCF 还提供了融入此绑定的示例。 有关此示例的详细信息，请参阅[与 ASMX Web 服务互操作](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)。  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>使用 WCF 客户端访问 WSE 3.0 Web 服务  
  
1.  运行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)创建 WSE 3.0 Web 服务的 WCF 客户端。  
  
     对于 WSE 3.0 Web 服务，创建 WCF 客户端。 因为 WSE 3.0 不支持 MEX 协议，因此不能使用该工具检索 Web 服务的安全要求。 应用程序开发人员必须为客户端添加安全设置。  
  
     有关创建 WCF 客户端的详细信息，请参阅[如何：创建客户端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
2.  创建一个类，表示可与 WSE 3.0 Web 服务进行通信的绑定。  
  
     下面的类是一部分[与 WSE 互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)示例：  
  
    1.  创建一个从 <xref:System.ServiceModel.Channels.Binding> 类派生的类。  
  
         下面的代码示例创建一个从 `WseHttpBinding` 类派生的名为 <xref:System.ServiceModel.Channels.Binding> 的类。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  向该类中添加属性，用以指定 WSE 服务使用的 WSE 完整断言、是否需要派生密钥、是否使用安全会话、是否需要签名确认以及消息保护设置。 在 WSE 3.0 中，完整断言指定客户端或 Web 服务的安全要求，类似于 WCF 中的一个绑定的身份验证模式。  
  
         下面的代码示例定义了 `SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext` 和 `MessageProtectionOrder` 属性，这些属性分别指定 WSE 完整断言、是否需要派生密钥、是否使用安全会话、是否需要签名确认以及消息保护设置。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  重写 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法以设置绑定属性。  
  
         下面的代码示例通过获取 `SecurityAssertion` 和 `MessageProtectionOrder` 属性的值来指定传输协议、消息编码和消息保护设置。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  在客户端应用程序代码中，添加设置绑定属性的代码。  
  
     下面的代码示例指定 WCF 客户端必须使用消息保护和身份验证，规定的 WSE 3.0`AnonymousForCertificate`关守安全断言。 此外，还需要安全会话和派生密钥。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>示例  
 下面的代码示例定义了一个自定义绑定，该绑定公开对应于 WSE 3.0 完整安全断言的各个属性的属性。 该自定义绑定，名为`WseHttpBinding`，然后用于指定与 WSSecurityAnonymous WSE 3.0 快速入门示例通信的 WCF 客户端的绑定属性。  

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.Binding>
- [与 WSE 互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
