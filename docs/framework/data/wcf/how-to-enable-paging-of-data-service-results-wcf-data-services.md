---
title: 如何：启用分页的数据服务结果 （WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 77dbeba89b352fa470ab0523a830db9175a1a21a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122897"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>如何：启用分页的数据服务结果 （WCF 数据服务）
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可以限制由数据服务查询返回的实体数。 页限制在初始化服务时调用的方法中定义，并可为每个实体集单独设置页限制。  
  
 启用分页后，源中的最后一项包含指向下一页数据的链接。 有关详细信息，请参阅[数据服务配置](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 本主题介绍如何修改数据服务以启用返回的 `Customers` 和 `Orders` 实体集的分页。 本主题中的示例使用 Northwind 示例数据服务。 此服务创建完成后[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>如何启用返回的 Customers 和 Orders 实体集的分页  
  
-   在数据服务的代码中，用下列代码替换 `InitializeService` 函数中的占位符代码：  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>请参阅

- [加载延迟的内容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [如何：加载分页结果](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
