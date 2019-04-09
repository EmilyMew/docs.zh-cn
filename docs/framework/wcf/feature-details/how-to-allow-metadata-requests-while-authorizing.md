---
title: 如何：授权时允许元数据请求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 4d549bb953ecdcbddd0ea4730a766538b2205d0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082667"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>如何：授权时允许元数据请求
自定义授权时，可能有必要允许处理对元数据的请求。 以下主题将演练验证此类请求的步骤。  
  
 有关 Windows Communication Foundation (WCF) 授权的详细信息，请参阅[授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>授权时允许元数据请求  
  
1.  创建 <xref:System.ServiceModel.ServiceAuthorizationManager> 类的扩展。  
  
2.  重写 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。 取决于是否允许授权，该方法返回 `true` 或 `false`。 有关当前过程的信息，请参见作为参数传递给该方法的 <xref:System.ServiceModel.OperationContext>。  
  
3.  重写时，检查协定名称、命名空间和操作，如在以下示例所示。 如果条件有效，然后返回 `true.`  
  
4.  使用扩展点利用类。 有关详细信息，请参阅[如何：创建自定义授权管理器服务](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示对 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法的重写。  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [使用标识模型管理声明和授权](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
