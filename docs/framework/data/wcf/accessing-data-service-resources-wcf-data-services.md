---
title: 访问数据服务资源（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, querying
- getting started, WCF Data Services
- querying the data service [WCF Data Service]
- WCF Data Services, getting started
- WCF Data Services, accessing data
ms.assetid: 9665ff5b-3e3a-495d-bf83-d531d5d060ed
ms.openlocfilehash: 6d4b0af7f20cbf932773df3ae226729a0a6c2500
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085864"
---
# <a name="accessing-data-service-resources-wcf-data-services"></a>访问数据服务资源（WCF 数据服务）
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支持[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]若要将数据公开为通过 Uri 进行寻址的资源的源。 这些资源表示的实体关系约定根据[实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)。 在此模型中，实体表示作为应用程序域中数据类型的数据操作单元，如客户、订单、项目和产品。 可以通过使用具象状态传输 (REST) 的语义（尤其是标准 HTTP 谓词 GET、PUT、POST 和 DELETE）访问和更改实体数据。  
  
## <a name="addressing-resources"></a>处理资源  
 在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 中，您可以通过使用 URI 对数据模型公开的任何数据进行寻址。 例如，下面的 URI 返回 Customers 实体集包含的所有实例的 Customer 实体类型的项的源：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers  
```  
  
 实体具有称为实体键的特殊属性。 实体键用于在实体集中唯一标识某个实体。 这样，您可以在实体集中对某种实体类型的特定实例进行寻址。 例如，下面的 URI 返回 Customer 实体类型的具有键值 `ALFKI` 的特定实例的项：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')  
```  
  
 也可以对实体实例的基元属性和复杂属性进行单独寻址。 例如，下面的 URI 返回一个包含特定客户的 `ContactName` 属性值的 XML 元素：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName  
```  
  
 如果在上面的 URI 中包括 `$value` 终结点，则只在响应消息中返回基元属性的值。 下面的示例只返回字符串“Maria Anders”，而不返回 XML 元素：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/ContactName/$value  
```  
  
 实体之间的关系在数据模型中由关联定义。 通过这些关联，可以使用实体实例的导航属性对相关实体进行寻址。 对于多对一的关系，导航属性可返回单个相关实体；对于一对多的关系，导航属性可返回一组相关实体。 例如，下面的 URI 返回一个作为与特定客户相关的所有订单集的源：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders  
```  
  
 通常为双向的关系由一对导航属性表示。 作为对前一示例中所示的关系的反转，下面的 URI 返回对特定 Order 实体所属的 Customer 实体的引用：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/Customer  
```  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 此外可以基于查询表达式的结果进行资源寻址。 这样，可以基于计算的表达式的资源集进行筛选。 例如，下面的 URI 对资源进行筛选以仅返回指定客户自 1997 年 9 月 22 日起已发货的订单：  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'  
```  
  
 有关详细信息，请参阅[OData:URI 约定](https://go.microsoft.com/fwlink/?LinkId=185564)。  
  
## <a name="system-query-options"></a>系统查询选项  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定义一组可用于传统的查询对资源执行操作，如筛选、 排序和分页的系统查询选项。 例如，下面的 URI 返回所有`Order`和相关`Order_Detail`实体，其中邮政编码尾号不`100`:  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')&$expand=Order_Details&$orderby=ShipCity  
```  
  
 返回源中的各项还按订单的 ShipCity 属性值进行排序。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支持以下[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]系统查询选项：  
  
|查询选项|描述|  
|------------------|-----------------|  
|`$orderby`|定义用于返回的源中的实体的默认排序顺序。 下面的查询按市/县对返回的客户源进行排序：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$orderby=Country,City`<br /><br /> 有关详细信息，请参阅[OData:OrderBy 系统查询选项 ($orderby)](https://go.microsoft.com/fwlink/?LinkId=186968)。|  
|`$top`|指定要包括在返回的源中的实体数。 下面的示例跳过前 10 个客户，然后返回接下来的 10 个客户：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 有关详细信息，请参阅[OData:Top 系统查询选项 ($top)](https://go.microsoft.com/fwlink/?LinkId=186969)。|  
|`$skip`|指定开始在源中返回实体前要跳过的实体数。 下面的示例跳过前 10 个客户，然后返回接下来的 10 个客户：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$skip=10&$top=10`<br /><br /> 有关详细信息，请参阅[OData:Skip 系统查询选项 ($skip)](https://go.microsoft.com/fwlink/?LinkId=186971)。|  
|`$filter`|定义一个基于特定条件对源中返回的实体进行筛选的表达式。 此查询选项支持一组用于计算筛选表达式的逻辑比较运算符、算术运算符和预定义查询函数。 下面示例返回邮政编码尾号不是 100 的所有订单：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Orders?$filter=not endswith(ShipPostalCode,'100')`<br /><br /> 有关详细信息，请参阅[OData:筛选系统查询选项 ($filter)](https://go.microsoft.com/fwlink/?LinkId=186972)。|  
|`$expand`|指定由查询返回哪些相关实体。 相关实体将作为源或内联项与查询返回的实体包含在一起。 下面的示例返回客户“ALFKI”的订单以及每个订单的项目详细信息：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$expand=Order_Details`<br /><br /> 有关详细信息，请参阅[OData:Expand 系统查询选项 ($expand)](https://go.microsoft.com/fwlink/?LinkId=186973)。|  
|`$select`|指定一个投影，用于定义在投影中返回的实体的属性。 默认情况下，在源中返回实体的所有属性。 下面的查询仅返回 `Customer` 实体的三个属性：<br /><br /> `http://services.odata.org/Northwind/Northwind.svc/Customers?$select=CustomerID,CompanyName,City`<br /><br /> 有关详细信息，请参阅[OData:选择系统查询选项 ($select)](https://go.microsoft.com/fwlink/?LinkID=186076)。|  
|`$inlinecount`|请求在源中包括源中返回的实体数的计数。 有关详细信息，请参阅[OData:Inlinecount 系统查询选项 ($inlinecount)](https://go.microsoft.com/fwlink/?LinkId=186975)。|  
  
## <a name="addressing-relationships"></a>对关系进行寻址  
 除了对实体集和实体实例进行寻址[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]还使您能够表示实体之间的关系的关联进行寻址。 若要创建或更改两个实体实例（例如与 Northwind 示例数据库中指定订单相关的发货方）之间的关系，必须使用此功能。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 支持`$link`运算符，专用于寻址的实体之间的关联。 例如，在 HTTP PUT 请求消息中指定下面的 URI 可将指定订单的发货方更改为新发货方。  
  
```  
http://services.odata.org/Northwind/Northwind.svc/Orders(10643)/$links/Shipper  
```  
  
 有关详细信息，请参阅[OData:项之间的链接进行寻址](https://go.microsoft.com/fwlink/?LinkId=187351)。  
  
## <a name="consuming-the-returned-feed"></a>使用返回的源  
 URI[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]资源可以由服务公开的地址实体数据。 在 Web 浏览器的地址字段中输入 URI 时[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]返回所请求资源的源表示形式。 有关详细信息，请参阅[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。 尽管 Web 浏览器可能可用于测试数据服务资源能否返回预期的数据，可以同时创建、 更新和删除数据的生产数据服务通常会访问应用程序代码或脚本编写语言在网页中的。 有关详细信息，请参阅[在客户端应用程序中使用数据服务](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)。  
  
## <a name="see-also"></a>请参阅

- [开放式数据协议网站（可能为英文网页）](https://go.microsoft.com/fwlink/?LinkID=182204)
