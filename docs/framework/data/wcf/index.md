---
title: WCF 数据服务 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 6910bfbc94f69292bb8c2a52bf3ebef8fcfb3a8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500234"
---
# <a name="wcf-data-services-45"></a>WCF 数据服务 4.5

WCF 数据服务 （以前称为"ADO.NET 数据服务"） 是一个组件，可创建使用服务的.NET framework[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]公开和使用的语义通过 Web 或 intranet 使用数据[具象状态传输 (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)。 OData 将数据公开为可通过 URI 进行寻址的资源。 通过使用标准 HTTP 谓词 GET、PUT、POST 和 DELETE 访问和更改数据。 OData 使用的实体关系约定[实体数据模型](../../../../docs/framework/data/adonet/entity-data-model.md)将资源公开为通过关联相关的实体集。

WCF 数据服务使用 OData 协议进行寻址以及更新资源。 这样一来，可以从任何支持 OData 的客户端访问这些服务。 OData 可以请求并通过使用众所周知的传输格式将数据写入资源：Atom、 交换和更新数据作为 XML 和 JavaScript 对象表示法 (JSON) 的标准的一组在 AJAX 应用程序中广泛使用的基于文本的数据交换格式。

WCF 数据服务可以公开源自各种源作为 OData 源的数据。 Visual Studio 工具使你更轻松地使用 ADO.NET 实体框架数据模型创建的基于 OData 的服务。 此外可以创建基于公共语言运行时 (CLR) 类，甚至基于后期绑定或非类型化数据的 OData 源。

WCF Data Services 还包括一组客户端库，一个用于常规.NET Framework 客户端应用程序，另一个专用于基于 Silverlight 的应用程序。 访问 OData 源从.NET Framework 和 Silverlight 之类的环境时，这些客户端库提供了基于对象的编程模型。

## <a name="where-should-i-start"></a>从何处开始？

具体取决于您的兴趣，请考虑以下主题之一中的 WCF Data Services 入门。

我希望直接开始使用...

- [快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [入门](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

- [Silverlight 快速入门](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Windows Phone 开发 Silverlight 快速入门](https://go.microsoft.com/fwlink/?LinkID=214535)

只需向我显示一些代码...

- [快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [如何：执行数据服务查询](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [如何：将数据绑定到 Windows Presentation Foundation 元素](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

我想要了解有关 OData 的详细信息...

- [白皮书：OData 简介](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Open Data Protocol 网站](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData:SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData:方面的常见问题](https://go.microsoft.com/fwlink/?LinkId=185867)

我想要观看一些视频...

- [WCF Data Services 初学者指南](https://go.microsoft.com/fwlink/?LinkId=220864)

- [WCF Data Services 开发人员视频](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData:开发人员网站](https://go.microsoft.com/fwlink/?LinkId=185866)

我想要查看端到端示例...

- [MSDN 示例库上的 WCF Data Services 文档示例](https://go.microsoft.com/fwlink/?LinkID=220865)

- [MSDN 示例库上的其他 WCF Data Services 示例](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData:SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

它如何与 Visual Studio 集成？

- [生成数据服务客户端库](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

- [创建数据服务](../../../../docs/framework/data/wcf/creating-the-data-service.md)

- [实体框架提供程序](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

我可以对它执行何种操作？

- [概述](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

- [白皮书：OData 简介](https://go.microsoft.com/fwlink/?LinkId=220867)

- [应用程序方案](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

我想要使用 Silverlight......

- [Silverlight 快速入门](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Silverlight 入门](https://go.microsoft.com/fwlink/?LinkId=148366)

我想要使用 LINQ......

- [查询数据服务](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

- [LINQ 注意事项](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [如何：执行数据服务查询](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

我仍需要了解一些更多信息...

- [WCF Data Services Team Blog](https://go.microsoft.com/fwlink/?LinkID=150511)（WCF Data Services 团队博客）

- [资源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

- [WCF Data Services 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Open Data Protocol 网站](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>本节内容

[概述](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

提供的功能和 WCF 数据服务中提供的功能的概述。

[什么是 WCF 数据服务 5.0 中的新增功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

介绍 WCF 数据服务和对新 OData 功能的支持中的新功能。

[入门](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

介绍如何公开和使用 WCF 数据服务使用 OData 源。

[定义 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

介绍如何创建和配置公开 OData 源的数据服务。

[WCF Data Services 客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

介绍如何使用客户端库使用 OData 源从.NET Framework 客户端应用程序。

## <a name="see-also"></a>请参阅

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)（表述性状态转移 (REST)）
