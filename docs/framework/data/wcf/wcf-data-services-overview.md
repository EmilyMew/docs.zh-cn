---
title: WCF 数据服务概述
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: b7e8d0842b705a2fc8897511e1b2e01441d9c6b9
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465836"
---
# <a name="wcf-data-services-overview"></a>WCF 数据服务概述
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支持使用来创建和使用的 Web 或 intranet 的数据服务[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 使您能够将数据公开为通过 Uri 进行寻址的资源。 这样，您就可以通过使用具象状态传输 (REST) 的语义（尤其是标准 HTTP 谓词 GET、PUT、POST 和 DELETE）来访问和更改数据。 本主题概述了 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定义的模式和做法，另外还介绍 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]提供的帮助在基于 .NET Framework 的应用程序中使用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的工具。  
  
## <a name="address-data-as-resources"></a>以资源形式对数据进行寻址  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 将数据公开为可通过 URI 进行寻址的资源。 基于实体数据模型的实体关系约定构造资源路径。 在此模型中，实体表示应用程序域，如客户、 订单、 项和产品中的数据的操作单元。 有关详细信息，请参阅[实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)。  
  
 在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 中，实体资源地址的形式为包含实体类型实例的实体集。 例如，URI`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders`返回的所有从订单`Northwind`与客户相关的数据服务`CustomerID`的值 `ALFKI.`  
  
 利用查询表达式，可以对资源执行传统的查询操作，如筛选、排序和分页。 例如，URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` 对资源进行筛选，以仅返回运费高于 50 美元的订单。 有关详细信息，请参阅[访问数据服务资源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)。  
  
## <a name="interoperable-data-access"></a>可互操作的数据访问  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 基于标准 Internet 协议来使数据服务与不使用.NET Framework 的应用程序进行互操作。 因为您可以使用标准 Uri 对数据进行寻址，应用程序可以访问和更改数据，通过使用具象状态传输 (REST)，尤其是标准 HTTP 谓词的语义 GET、 PUT、 POST 和 DELETE。 这样您就可以从任何可分析和访问通过标准 HTTP 协议传输的数据的客户端访问这些服务。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定义一组对 Atom 发布协议 (AtomPub) 的扩展。 它支持采用多种数据格式的 HTTP 请求和响应，以适应各种客户端应用程序和平台。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 源可以采用 Atom、JavaScript 对象表示法 (JSON) 以及纯 XML 格式表示数据。 尽管 Atom 是默认格式，但源的格式会在 HTTP 请求的标头中指定。 有关详细信息，请参阅[OData:Atom 格式](https://go.microsoft.com/fwlink/?LinkID=185794)和[OData:JSON 格式](https://go.microsoft.com/fwlink/?LinkID=185795)。  
  
 发布的数据时[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]馈送，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]依赖于其他现有的 Internet 功能执行诸如缓存和身份验证等操作。 若要实现此目的，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]与现有宿主应用程序和服务，如 ASP.NET、 Windows Communication Foundation (WCF) 和 Internet 信息服务 (IIS) 集成。  
  
## <a name="storage-independence"></a>存储独立性  
 尽管可基于实体关系模型对资源进行寻址，但是无论基础数据源是什么，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]都会公开 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 源。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 接受针对 URI 标识的资源的 HTTP 请求后，会对该请求进行反序列化，并将该请求的表示形式传递给 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供程序。 此提供程序将该请求转换为特定于数据源的格式，并在基础数据源上执行该请求。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]通过将对 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 规定的资源进行寻址的概念模型与基础数据源的具体架构分离，实现存储独立性。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 与 ADO.NET 实体框架集成，使您可以创建公开关系数据的数据服务。 可以使用实体数据模型工具创建包含以实体形式存在的可寻址资源的数据模型，同时定义此模型与基础数据库中表之间的映射。 有关详细信息，请参阅[实体框架提供程序](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 此外可以创建公开返回的一个实现所有的数据结构的数据服务<xref:System.Linq.IQueryable%601>接口。 这样您就可以创建公开 .NET Framework 类型中数据的数据服务。 当您也实现 <xref:System.Data.Services.IUpdatable> 接口时，支持创建、更新和删除操作。 有关详细信息，请参阅[反射提供程序](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)。  
  
 为举例说明了如何[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]集成，使用这些数据提供程序，请参阅后面本主题的体系结构关系图。  
  
## <a name="custom-business-logic"></a>自定义业务逻辑  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 轻松将自定义业务逻辑添加到数据服务通过服务操作和侦听器。 服务操作是在可通过 URI（采用与数据资源相同的形式）进行寻址的服务器上定义的方法。 服务操作还可以使用查询表达式语法对操作返回的数据进行筛选、排序和分页。 例如，URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` 表示对 Northwind 数据服务上的名为 `GetOrdersByCity` 的服务操作的调用，此调用将返回来自伦敦的客户的订单，并且会对结果进行分页并按 `OrderDate` 排序。 有关详细信息，请参阅[服务操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)。  
  
 利用侦听器，可以将自定义应用程序逻辑集成到数据服务对请求或响应消息的处理中。 在指定的实体集上执行查询、插入、更新或删除操作时，将调用相应的侦听器。 然后，侦听器可能会更改数据、执行授权策略或者甚至终止操作。 必须为由数据服务公开的给定实体集显式注册侦听器方法。 有关详细信息，请参阅[侦听器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。  
  
## <a name="client-libraries"></a>客户端库  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 定义一组统一模式来与数据服务交互。 这提供了创建基于这些服务，如更加轻松地使用数据服务的客户端库的可重用组件的机会。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包括基于 .NET Framework 和基于 Silverlight 的客户端应用程序的客户端库。 通过这些客户端库，可以使用 .NET Framework 对象与数据服务进行交互。 它们还支持基于对象的查询和 LINQ 查询、加载相关对象、更改跟踪和标识解析。 有关详细信息，请参阅[WCF Data Services 客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。  
  
 除了[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]客户端库使用.NET Framework 和 Silverlight，附带有其他客户端库，使您能够使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]客户端应用程序，如 PHP、 AJAX 和 Java 应用程序中的源。 有关详细信息，请参阅[OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## <a name="architecture-overview"></a>体系结构概述  
 下图演示了[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]体系结构用于公开[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]源和中使用这些源[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-启用客户端库：  
  
 ![显示 WCF 数据服务体系结构关系图的屏幕截图。](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>请参阅
- [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)
- [入门](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [定义 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [访问数据服务资源 （WCF 数据服务）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [WCF Data Services 客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)（表述性状态转移 (REST)）
