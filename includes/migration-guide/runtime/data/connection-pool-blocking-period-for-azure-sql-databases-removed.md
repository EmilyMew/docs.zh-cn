---
ms.openlocfilehash: 9605352c66f85b6942ba24942cb07c88bdd81f2a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760600"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>已删除 Azure SQL 数据库的连接池锁定期

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6.2 起，对于发送到已知 Azure SQL 数据库（*.database.windows.net、*.database.chinacloudapi.cn、*.database.usgovcloudapi.net、*.database.cloudapi.de）的打开连接请求，删除了连接池锁定期且不会缓存打开连接错误。 在出现暂时连接错误后随即重试连接打开请求。 此更改允许立即重新尝试打开 Azure SQL 数据库的连接，从而改进了已启用云的应用的性能。 对于其他所有连接尝试，连接池阻止时间段还会继续强制执行。<p/>在 .NET Framework 4.6.1 和早期版本中，当应用在连接到数据库过程中遇到暂时性连接失败时，无法快速重试连接，因为连接池会缓存错误，并在 5 秒至 1 分钟后重新引发该错误。 有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md)。 这种行为会给 Azure SQL 数据库连接带来问题，因为经常会因暂时性错误而导致连接失败，这些错误通常在几秒内便会恢复。 连接池阻止功能意味着，应用在很长一段时间内都无法连接到数据库，即使数据库可用且应用需要在几秒钟内呈现也不行。|
|建议|如果不需要此行为，可以通过设置 .NET Framework 4.6.2 中引入的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> 属性配置连接池锁定期。 该属性的值属于 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> 枚举，可采用以下三个值中的任意一个：<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>可以通过将 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> 属性设置为 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> 来还原以前的行为。|
|范围|次要|
|版本|4.6.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

