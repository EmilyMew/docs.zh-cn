---
title: 缓解：池阻止时间段
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c90a75ebbb9e4bc6248aadd709be8b5285ecd6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409115"
---
# <a name="mitigation-pool-blocking-period"></a>缓解：池阻止时间段
与 Azure SQL 数据库的连接已删除连接池阻止时间段。  
  
## <a name="additional-description"></a>其他说明  
 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和早期版本中，当应用在连接到数据库过程中遇到暂时性连接失败时，无法快速重试连接，因为连接池会缓存错误，并在 5 秒至 1 分钟后重新引发该错误。有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。 这种行为会给 Azure SQL 数据库连接带来问题，因为经常会因暂时性错误而导致连接失败，这些错误通常在几秒内便会恢复。 连接池阻止功能意味着，应用在很长一段时间内都无法连接到数据库，即使数据库可用也不行。 对于连接到 Azure SQL 数据库以及需要在几秒内呈现的 Web 应用，这种行为带来的问题尤为明显。  
  
 对于发送到已知 Azure SQL 数据库（*.database.windows.net、\*.database.chinacloudapi.cn、\*.database.usgovcloudapi.net、\*.database.cloudapi.de）的打开连接请求（开头为 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]），将不会缓存打开连接错误。 对于其他所有连接尝试，连接池阻止时间段还会继续强制执行。  
  
## <a name="impact"></a>影响  
 此更改允许立即重新尝试打开 Azure SQL 数据库的连接，从而改进了已启用云的应用的性能。  
  
## <a name="mitigation"></a>缓解  
 对于受到此更改不利影响的应用，连接池阻止时间段可通过设置新 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> 属性进行配置。  该属性的值属于 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> 枚举，可采用以下三个值中的任意一个：  
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
-   <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 可以通过将 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> 属性设置为 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> 来还原以前的行为。  
  
## <a name="see-also"></a>请参阅
- [运行时更改](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
