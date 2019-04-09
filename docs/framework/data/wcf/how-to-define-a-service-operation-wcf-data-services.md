---
title: 如何：定义服务操作 （WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 75691a49624c179166d18225fac9fdc6c17a2308
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138094"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>如何：定义服务操作 （WCF 数据服务）
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 公开在服务器作为服务操作定义的方法。 服务操作允许数据服务以提供通过在服务器上定义的方法的 URI 的访问权限。 若要定义服务操作，应用 [`WebGet]`或`[WebInvoke]`属性为该方法。 若要支持查询运算符，服务操作必须返回<xref:System.Linq.IQueryable%601>实例。 服务操作可以通过 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> 的 <xref:System.Data.Services.DataService%601> 属性访问基础数据源。 有关详细信息，请参阅[服务操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。  
  
 本主题中的示例定义一个名为 `GetOrdersByCity` 的服务操作，该操作返回 <xref:System.Linq.IQueryable%601> 和相关 `Orders` 对象的经筛选后的 `Order_Details` 实例。 该示例访问作为 Northwind 示例数据服务数据源的 <xref:System.Data.Objects.ObjectContext> 实例。 此服务创建完成后[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>在 Northwind 数据服务中定义服务操作  
  
1.  在 Northwind 数据服务项目中，打开 Northwind.svc 文件。  
  
2.  在 `Northwind` 类中，定义一个名为 `GetOrdersByCity` 的服务操作方法，如下所示：  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  在 `InitializeService` 类的 `Northwind` 方法中，添加以下代码以支持对服务操作的访问：  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>查询 GetOrdersByCity 服务操作  
  
-   在 Web 浏览器中，输入以下 URI 之一以调用在以下示例中定义的服务操作：  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>示例  
 以下示例对 Northwind 数据服务实现一个名为 `GetOrderByCity` 的服务操作。 此操作根据提供的城市名称使用 ADO.NET 实体框架返回一组 `Orders` 和相关 `Order_Details` 对象，以作为 <xref:System.Linq.IQueryable%601> 实例。  
  
> [!NOTE]
>  由于此方法返回了一个 <xref:System.Linq.IQueryable%601> 实例，因此该服务操作终结点支持查询运算符。  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>请参阅

- [定义 WCF 数据服务](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
