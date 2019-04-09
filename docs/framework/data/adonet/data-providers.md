---
title: .NET Framework 数据提供程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: f821088375bf1df01e75de5e0c226334baca113f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074022"
---
# <a name="net-framework-data-providers"></a>.NET Framework 数据提供程序
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序用于连接到数据库、执行命令和检索结果。 这些结果将被直接处理，放置在 <xref:System.Data.DataSet> 中以便根据需要向用户公开、与多个源中的数据组合，或在层之间进行远程处理。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序是轻量，创建一个最小层之间的数据源和代码，而无需牺牲功能提高性能。  
  
 下表列出了 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中所包含的数据提供程序。  
  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据访问接口|描述|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 SQL Server 的数据提供程序|提供 Microsoft SQL Server 的数据访问。 使用 <xref:System.Data.SqlClient> 命名空间。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 OLE DB 的数据提供程序|提供对使用 OLE DB 公开的数据源中数据的访问。 使用 <xref:System.Data.OleDb> 命名空间。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 ODBC 的数据提供程序|提供对使用 ODBC 公开的数据源中数据的访问。 使用 <xref:System.Data.Odbc> 命名空间。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 Oracle 的数据提供程序|适用于 Oracle 数据源。 用于 Oracle 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序支持 Oracle 客户端软件 8.1.7 和更高版本，并使用 <xref:System.Data.OracleClient> 命名空间。|  
|EntityClient 提供程序|提供对实体数据模型 (EDM) 应用程序的数据访问。 使用 <xref:System.Data.EntityClient> 命名空间。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序适用于 SQL Server Compact 4.0。|提供的 Microsoft SQL Server Compact 4.0 数据访问。 使用 [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) 命名空间。|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>.NET Framework 数据提供程序的核心对象  
 下表概述了组成 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序的四个核心对象。  
  
|对象|描述|  
|------------|-----------------|  
|`Connection`|建立与特定数据源的连接。 所有 `Connection` 对象的基类均为 <xref:System.Data.Common.DbConnection> 类。|  
|`Command`|对数据源执行命令。 公开 `Parameters` ，并可在 `Transaction` 范围内从 `Connection`执行。 所有 `Command` 对象的基类均为 <xref:System.Data.Common.DbCommand> 类。|  
|`DataReader`|从数据源中读取只进且只读的数据流。 所有 `DataReader` 对象的基类均为 <xref:System.Data.Common.DbDataReader> 类。|  
|`DataAdapter`|使用数据源填充 `DataSet` 并解决更新。 所有 `DataAdapter` 对象的基类均为 <xref:System.Data.Common.DbDataAdapter> 类。|  
  
 除了此文档前面的表中所列出的核心类之外， [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序还包含下表中列出的类。  
  
|对象|描述|  
|------------|-----------------|  
|`Transaction`|将命令登记在数据源处的事务中。 所有 `Transaction` 对象的基类均为 <xref:System.Data.Common.DbTransaction> 类。 ADO.NET 还使用 <xref:System.Transactions> 命名空间中的类提供对事务的支持。|  
|`CommandBuilder`|一个帮助器对象，它自动生成 `DataAdapter` 的命令属性或从存储过程中派生参数信息，并填充 `Parameters` 对象的 `Command` 集合。 所有 `CommandBuilder` 对象的基类均为 <xref:System.Data.Common.DbCommandBuilder> 类。|  
|`ConnectionStringBuilder`|一个帮助器对象，它提供一种用于创建和管理由 `Connection` 对象使用的连接字符串的内容的简单方法。 所有 `ConnectionStringBuilder` 对象的基类均为 <xref:System.Data.Common.DbConnectionStringBuilder> 类。|  
|`Parameter`|定义命令和存储过程的输入、输出和返回值参数。 所有 `Parameter` 对象的基类均为 <xref:System.Data.Common.DbParameter> 类。|  
|`Exception`|在数据源中遇到错误时返回。 对于在客户端遇到的错误， [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序会引发一个 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 异常。 所有 `Exception` 对象的基类均为 <xref:System.Data.Common.DbException> 类。|  
|`Error`|公开数据源返回的警告或错误中的信息。|  
|`ClientPermission`|为 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序代码访问安全属性而提供。 所有 `ClientPermission` 对象的基类均为 <xref:System.Data.Common.DBDataPermission> 类。|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>用于 SQL Server 的 .NET Framework 数据提供程序 (SqlClient)  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server (SqlClient) 数据提供程序使用其自己的协议来与 SQL Server 通信。 它是轻量，并执行良好，因为它经过优化，可添加一个 OLE DB 或开放式数据库连接 (ODBC) 层不直接访问 SQL Server。 以下图形成鲜明对比[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]使用 SQL Server 的数据提供程序[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]OLE DB 数据提供程序。 用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序通过 OLE DB 服务组件（它提供连接池和事务服务）和用于数据源的 OLE DB 访问接口与 OLE DB 数据源进行通信。  
  
> [!NOTE]
>  用于 ODBC 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序具有与用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序相似的体系结构；例如，它会对 ODBC 服务组件进行调用。  
  
 ![数据访问接口](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
用于 SQL Server 的 .NET Framework 数据提供程序和用于 OLE DB 的 .NET Framework 数据提供程序的比较  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]数据提供程序的 SQL Server 类位于<xref:System.Data.SqlClient>命名空间。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server 的数据提供程序支持本地事务和分布式事务两者。 对于分布式事务， [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server，默认情况下，数据提供程序自动在事务中登记，并从 Windows Component Services 获取事务详细信息或<xref:System.Transactions>。 有关详细信息，请参阅[事务和并发性](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下面的代码示例演示如何将 `System.Data.SqlClient` 命名空间包括在您的应用程序中。  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>用于 OLE DB 的 .NET Framework 数据提供程序  
 用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序 (OleDb) 通过 COM 互操作使用本机 OLE DB 来启用数据访问。 用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序支持本地事务和分布式事务。 对于分布式事务，用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序在默认情况下会自动在事务中登记，并从 Windows Component Services 获取事务详细信息。 有关详细信息，请参阅[事务和并发性](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下表演示已使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]进行测试的提供程序。  
  
|驱动程序|提供程序|  
|------------|--------------|  
|SQLOLEDB|SQL Server 的 Microsoft OLE DB 提供程序|  
|MSDAORA|用于 Oracle 的 Microsoft OLE DB 提供程序|  
|Microsoft.Jet.OLEDB.4.0|用于 Microsoft Jet 的 OLE DB 访问接口|  
  
> [!NOTE]
>  建议不要将 Access (Jet) 数据库用作多线程应用程序（如 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 应用程序）的数据源。 如果必须将 Jet 用作 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 应用程序的数据源，请注意连接到 Access 数据库的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 应用程序可能会遇到连接问题。  
  
 用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序不支持 OLE DB 2.5 版接口。 需要对 OLE DB 2.5 接口的支持的 OLE DB 访问接口将无法与用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序一起正常工作。 这包括适用于 Exchange 的 Microsoft OLE DB 访问接口和用于 Internet 发布的 Microsoft OLE DB 访问接口。  
  
 用于 OLE DB 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序不与用于 ODBC 的 OLE DB 访问接口 (MSDASQL) 一起使用。 若要使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]访问 ODBC 数据源，请使用用于 ODBC 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 OLE DB 类的数据提供程序位于<xref:System.Data.OleDb>命名空间。 下面的代码示例演示如何将 `System.Data.OleDb` 命名空间包括在您的应用程序中。  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>用于 ODBC 的 .NET Framework 数据提供程序  
 用于 ODBC 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序 (Odbc) 使用本机 ODBC 驱动程序管理器 (DM) 来启用数据访问。 ODBC 数据提供程序支持本地事务和分布式事务两者。 对于分布式事务，ODBC 提供程序在默认情况下会自动在事务中登记，并从 Windows Component Services 获取事务详细信息。 有关详细信息，请参阅[事务和并发性](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 下表演示已使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]进行测试的 ODBC 驱动程序。  
  
|驱动程序|  
|------------|  
|SQL Server|  
|Microsoft ODBC for Oracle|  
|Microsoft Access 驱动程序 (*.mdb)|  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 对于 ODBC 类的数据提供程序位于<xref:System.Data.Odbc>命名空间。  
  
 下面的代码示例演示如何将 `System.Data.Odbc` 命名空间包括在您的应用程序中。  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  用于 ODBC 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序需要 MDAC 2.6 或更高版本，建议使用 MDAC 2.8 SP1。 可以从 [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173)（数据访问和存储开发中心）下载 MDAC 2.8 SP1。  
  
## <a name="net-framework-data-provider-for-oracle"></a>用于 Oracle 的 .NET Framework 数据提供程序  
 用于 Oracle 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序 (OracleClient) 通过 Oracle 客户端连接软件启用对 Oracle 数据源的数据访问。 该数据提供程序支持 Oracle 客户端软件 8.1.7 版或更高版本。 该数据提供程序支持本地事务和分布式事务两者。 有关详细信息，请参阅[事务和并发性](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)。  
  
 用于 Oracle 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序要求系统上安装有 Oracle 客户端软件（8.1.7 版或更高版本），才能连接到 Oracle 数据源。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 Oracle 类的数据提供程序位于<xref:System.Data.OracleClient>命名空间，并包含在`System.Data.OracleClient.dll`程序集。 当编译使用该数据提供程序的应用程序时，必须同时引用 `System.Data.dll` 和 `System.Data.OracleClient.dll` 。  
  
 下面的代码示例演示如何将 `System.Data.OracleClient` 命名空间包括在您的应用程序中。  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>选择 .NET Framework 数据提供程序  
 根据您的应用程序的设计和数据源的不同，您对 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序的选择可改进您的应用程序的性能、功能和完整性。 下表讨论每个 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序的优势和局限性。  
  
|提供程序|说明|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 SQL Server 的数据提供程序|建议使用 Microsoft SQL Server 的中间层应用程序。<br /><br /> 建议使用 Microsoft 数据库引擎 (MSDE) 或 SQL Server 的单层应用程序。<br /><br /> 建议为 SQL Server (SQLOLEDB) 与 OLE DB 访问接口使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]OLE DB 数据提供程序。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 OLE DB 的数据提供程序|对于 SQL Server，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]而不是此提供程序建议使用 SQL Server 的数据提供程序。<br /><br /> 建议用于使用 Microsoft Access 数据库的单层应用程序。 不建议将 Access 数据库用于中间层应用程序。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 ODBC 的数据提供程序|建议用于使用 ODBC 数据源的中间层应用程序和单层应用程序。|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 用于 Oracle 的数据提供程序|建议用于使用 Oracle 数据源的中间层应用程序和单层应用程序。|  
  
## <a name="entityclient-provider"></a>EntityClient 提供程序  
 EntityClient 提供程序可用来基于实体数据模型 (EDM) 访问数据。 与其他 .NET Framework 数据提供程序不同，该提供程序不直接与数据源进行交互， 而是使用实体 SQL 与基础数据提供程序进行通信。 有关详细信息，请参阅[针对实体框架的 EntityClient Provider](./ef/entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="see-also"></a>请参阅

- [ADO.NET 概述](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
