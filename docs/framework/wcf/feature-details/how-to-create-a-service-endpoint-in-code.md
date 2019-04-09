---
title: 如何：在代码中创建服务终结点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 0b51018a5940e01b38b00addb762fa6504495a4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139862"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a>如何：在代码中创建服务终结点
在本示例中，将为计算器服务定义一个 `ICalculator` 协定，在 `CalculatorService` 类中实现该服务，然后在代码中定义其终结点（在这段代码中还指定该服务必须使用 <xref:System.ServiceModel.BasicHttpBinding> 类）。  
  
 通常，最佳做法是以声明方式在配置中指定绑定和地址信息，而不是在代码中强制指定。 在代码中定义终结点通常是不可行的，因为已部署服务的绑定和地址通常与在部署服务时所用的绑定和地址不同。 一般说来，通过将绑定和寻址信息放置在代码之外，无需重新编译或重新部署应用程序即可更改这些信息。  
  
#### <a name="to-create-a-service-endpoint-in-code"></a>在代码中创建服务终结点  
  
1.  创建定义服务协定的接口。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  实现在步骤 1 中定义的服务协定。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  在主机应用程序中，创建该服务的基址以及要用于该服务的绑定。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  创建宿主并调用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29> 或其他重载之一来添加宿主的服务终结点。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     若要在代码中指定绑定，而不使用运行时提供的默认终结点，请在创建 <xref:System.ServiceModel.ServiceHost> 时将基址传递给构造函数，并且不调用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>。  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     有关默认终结点的详细信息，请参阅[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)并[WCF 服务的简化配置](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
## <a name="see-also"></a>请参阅

- [如何：在代码中指定服务绑定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
