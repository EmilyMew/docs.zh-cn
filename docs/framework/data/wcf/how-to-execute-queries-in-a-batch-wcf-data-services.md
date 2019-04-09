---
title: 如何：在批处理 （WCF 数据服务） 中执行查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: a917659092890c95dfd65ede358d9c4b5a0e62cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117905"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>如何：在批处理 （WCF 数据服务） 中执行查询
通过使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]客户端库，可以在单个批处理中执行多个查询针对数据服务。 有关详细信息，请参阅[批处理操作](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)。  
  
 本主题中的示例使用罗斯文示例数据服务和自动生成的客户端数据服务类。 完成后，将创建此服务和客户端数据类[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何调用 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法来执行一个 <xref:System.Data.Services.Client.DataServiceRequest%601> 对象数组，该数组包含从 Northwind 数据服务同时返回 `Customers` 和 `Products` 对象的查询。 此示例将枚举返回的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 中的 <xref:System.Data.Services.Client.DataServiceResponse> 对象的集合，并且还会枚举每个 <xref:System.Data.Services.Client.QueryOperationResponse%601> 中包含的对象的集合。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>请参阅

- [WCF 数据服务客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
