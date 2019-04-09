---
title: 如何：加载相关的实体 （WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 7687378ae2a6c7d8021acc53b19544206ee0cc84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092625"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>如何：加载相关的实体 （WCF 数据服务）
如果需要在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中加载关联实体，可以使用 <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> 类的 <xref:System.Data.Services.Client.DataServiceContext> 方法。 此外可以使用<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>方法<xref:System.Data.Services.Client.DataServiceQuery%601>要求，在同一查询响应中积极加载相关的实体。  
  
 本主题中的示例使用罗斯文示例数据服务和自动生成的客户端数据服务类。 完成后，将创建此服务和客户端数据类[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何显式加载与每个返回的 `Customer` 实例相关的 `Orders`。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法返回属于由查询返回的 `Order Details` 的 `Orders`。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>请参阅

- [查询数据服务](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
