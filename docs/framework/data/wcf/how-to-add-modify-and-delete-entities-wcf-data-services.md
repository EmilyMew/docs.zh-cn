---
title: 如何：添加、 修改和删除实体 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
ms.openlocfilehash: 5816cb6a765a7cdf49aca9ac50461a4e50e6df14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122182"
---
# <a name="how-to-add-modify-and-delete-entities-wcf-data-services"></a>如何：添加、 修改和删除实体 (WCF Data Services)
与[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]客户端库，您可以创建、 更新和删除实体数据的数据服务中的对象执行等效操作<xref:System.Data.Services.Client.DataServiceContext>。 有关详细信息，请参阅[更新数据服务](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 本主题中的示例使用罗斯文示例数据服务和自动生成的客户端数据服务类。 完成后，将创建此服务和客户端数据类[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建一个新的对象实例，然后对 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> 调用 <xref:System.Data.Services.Client.DataServiceContext> 方法以创建上下文中的项。 调用 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法时，HTTP POST 消息将会发送到数据服务。  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## <a name="example"></a>示例  
 下面的示例检索和修改现有的对象，然后对 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 调用 <xref:System.Data.Services.Client.DataServiceContext> 方法以将上下文中的项标记为已更新。 调用 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法时，HTTP MERGE 消息将会发送到数据服务。  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## <a name="example"></a>示例  
 下面的示例对 <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> 调用 <xref:System.Data.Services.Client.DataServiceContext> 方法以将上下文中的项标记为删除。 调用 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法时，HTTP DELETE 消息将会发送到数据服务。  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## <a name="example"></a>示例  
 下面的示例创建一个新的对象实例，然后对 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 调用 <xref:System.Data.Services.Client.DataServiceContext> 方法以创建上下文中的项以及指向相关订单的链接。 调用 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法时，HTTP POST 消息将会发送到数据服务。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="see-also"></a>请参阅

- [WCF 数据服务客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [如何：将现有实体附加到 DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)
- [如何：定义实体关系](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)
- [批处理操作](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
