---
title: 检索数据库架构信息
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 885d3c9ad61c9099c960ddb0c0f77fa8a98dbefa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133700"
---
# <a name="retrieving-database-schema-information"></a>检索数据库架构信息
从数据库获取架构信息通过架构发现过程来完成。 架构发现，应用程序可以请求托管提供程序查找并返回有关数据库架构的信息也称为*元数据*，给定数据库。 不同的数据库架构元素（例如表、列和存储过程）通过架构集合进行公开。 每个架构集合包含所使用的提供程序特定的各种架构信息。  
  
 每个.NET Framework 托管提供程序实现**GetSchema**中的方法**连接**类，并从返回的架构信息**GetSchema**方法采用的形式<xref:System.Data.DataTable>。 **GetSchema**方法是重载的方法，提供可选参数来指定架构集合返回，并限制返回的信息量。  
  
 提供.NET Framework 数据提供程序的 OLE DB、 ODBC、 Oracle 和 SqlClient **GetSchemaTable**方法，它返回描述列元数据的 DataTable **DataReader**。  
  
 适用于 OLE DB 的 .NET Framework 数据提供程序还使用 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 对象的 <xref:System.Data.OleDb.OleDbConnection> 方法来公开架构信息。 作为参数， **GetOleDbSchemaTable**采用<xref:System.Data.OleDb.OleDbSchemaGuid>，它标识要返回架构信息并对这些限制的数组返回的列。 **GetOleDbSchemaTable**返回<xref:System.Data.DataTable>填充的请求的架构信息。  
  
## <a name="in-this-section"></a>本节内容  
 [GetSchema 和架构集合](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 介绍**GetSchema**方法以及如何使用它来检索和限制数据库中的架构信息。  
  
 架构限制  
 描述可以用于架构限制**GetSchema**。  
  
 [公共架构集合](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 描述所有 .NET Framework 托管提供程序均支持的所有通用架构集合。  
  
 [SQL Server 架构集合](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 描述适用于 SQL Server 的 .NET Framework 提供程序支持的架构集合。  
  
 [Oracle 架构集合](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 描述适用于 Oracle 的 SQL Server .NET Framework 提供程序支持的架构集合。  
  
 [ODBC 架构集合](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 描述 ODBC 驱动程序的架构集合。  
  
 [OLE DB 架构集合](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 描述 OLE DB 提供程序的架构集合。  
  
## <a name="reference"></a>参考  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 介绍**GetSchema**方法的<xref:System.Data.Common.DbConnection>类。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 介绍**GetSchema**方法的<xref:System.Data.Odbc.OdbcConnection>类。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 介绍**GetSchema**方法的<xref:System.Data.OleDb.OleDbConnection>类。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 介绍**GetSchema**方法的<xref:System.Data.OracleClient.OracleConnection>类。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 介绍**GetSchema**方法的<xref:System.Data.SqlClient.SqlConnection>类。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 介绍**GetSchemaTable**方法的<xref:System.Data.Common.DbDataReader>类。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 介绍**GetSchemaTable**方法的<xref:System.Data.Odbc.OdbcDataReader>类。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 介绍**GetSchemaTable**方法的<xref:System.Data.OleDb.OleDbDataReader>类。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 介绍**GetSchemaTable**方法的<xref:System.Data.OracleClient.OracleDataReader>类。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 介绍**GetSchemaTable**方法的<xref:System.Data.SqlClient.SqlDataReader>类。  
  
## <a name="see-also"></a>请参阅

- [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
