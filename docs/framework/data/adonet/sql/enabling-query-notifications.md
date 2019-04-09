---
title: 启用查询通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: a2227b33c7caacdd04c7bf50082bb0cfab7f3302
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113940"
---
# <a name="enabling-query-notifications"></a>启用查询通知
使用查询通知的应用程序有一组通用的需求。 必须正确配置数据源才能支持 SQL 查询通知，并且用户必须具有正确的客户端和服务器端权限。  
  
 要使用查询通知，必须符合下列条件：  
  
-   对数据库启用查询通知。  
  
-   确保用于连接数据库的用户 ID 具有必要的权限。  
  
-   使用 <xref:System.Data.SqlClient.SqlCommand> 对象执行有效的 SELECT 语句，包含关联的通知对象 — <xref:System.Data.SqlClient.SqlDependency> 或 <xref:System.Data.Sql.SqlNotificationRequest>。  
  
-   提供所监视的数据更改时用于处理通知的代码。  
  
## <a name="query-notifications-requirements"></a>查询通知需求  
 仅对满足一系列特定要求的 SELECT 语句支持查询通知。 下表提供指向“SQL Server 联机丛书”中的 Service Broker 和“查询通知”文档的链接。  
  
 **SQL Server 文档**  
  
-   [创建通知查询](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
-   [Service Broker 的安全注意事项](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
-   [Security and Protection (Service Broker)（安全性和保护 (Service Broker)）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
-   [Security Considerations for Notifications Services（Notification Services 的安全注意事项）](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
-   [Query Notification Permissions（查询通知权限）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
-   [International Considerations for Service Broker（Service Broker 的国际化注意事项）](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
-   [Solution Design Considerations (Service Broker)（解决方案设计注意事项 (Service Broker)）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
-   [Service Broker 开发人员信息中心](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
-   [Developer's Guide (Service Broker)（开发人员指南 (Service Broker)）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>启用查询通知运行示例代码  
 若要上启用 Service Broker **AdventureWorks**数据库使用 SQL Server Management Studio 中，执行以下 TRANSACT-SQL 语句：  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 若要此查询通知示例正确运行，必须在数据库服务器上执行下面的 Transact-SQL 语句。  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>查询通知权限  
 执行请求通知的命令的用户必须在服务器上具有 SUBSCRIBE QUERY NOTIFICATIONS 数据库权限。  
  
 在部分信任情况下运行的客户端代码要求 <xref:System.Data.SqlClient.SqlClientPermission>。  
  
 下面的代码创建一个 <xref:System.Data.SqlClient.SqlClientPermission> 对象，将 <xref:System.Security.Permissions.PermissionState> 设置为 <xref:System.Security.Permissions.PermissionState.Unrestricted>。 如果尚未为调用堆栈中的所有高级调用方授予该权限，则 <xref:System.Security.CodeAccessPermission.Demand%2A> 将在运行时强制引发 <xref:System.Security.SecurityException>。  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>选择通知对象  
 查询通知 API 提供两个用于处理通知的对象：<xref:System.Data.SqlClient.SqlDependency> 和 <xref:System.Data.Sql.SqlNotificationRequest>。 通常情况下，大多数非 ASP.NET 应用程序应使用 <xref:System.Data.SqlClient.SqlDependency> 对象。 ASP.NET 应用程序应使用更高级别的 <xref:System.Web.Caching.SqlCacheDependency>，以便包装 <xref:System.Data.SqlClient.SqlDependency> 并为管理通知和缓存对象提供框架。  
  
### <a name="using-sqldependency"></a>使用 SqlDependency  
 要使用 <xref:System.Data.SqlClient.SqlDependency>，必须对所使用的 SQL Server 数据库启用 Service Broker，并且用户必须具有接收通知的权限。 Service Broker 对象（例如通知队列）已预定义。  
  
 此外，<xref:System.Data.SqlClient.SqlDependency> 会自动启动一个辅助线程以在通知发布到队列中时处理这些通知；它还会分析 Service Broker 消息，将此信息作为事件自变量数据公开。 <xref:System.Data.SqlClient.SqlDependency> 必须通过调用来初始化`Start`方法建立到数据库的依赖项。 此方法是静态方法，在为每个所需的数据库连接初始化应用程序期间只需调用一次。 必须在应用程序终止时为执行的每个相关连接调用 `Stop` 方法。  
  
### <a name="using-sqlnotificationrequest"></a>使用 SqlNotificationRequest  
 相对而言，<xref:System.Data.Sql.SqlNotificationRequest> 要求您自己实现整个侦听基础结构。 此外，必须定义队列所支持的所有支持 Service Broker 对象（例如队列、服务和消息类型）。 如果应用程序要求特殊的通知消息或通知行为，或应用程序是更大的服务中介应用程序的一部分，此手动方法非常有用。  
  
## <a name="see-also"></a>请参阅

- [SQL Server 中的查询通知](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
