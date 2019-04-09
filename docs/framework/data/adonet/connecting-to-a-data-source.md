---
title: 连接到 ADO.NET 中的数据源
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083707"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>连接到 ADO.NET 中的数据源
在 ADO.NET 中，使用**连接**对象以连接到特定的数据源，通过提供必要的身份验证连接字符串中的信息。 **连接**您使用的对象取决于数据源的类型。  
  
 随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 <xref:System.Data.Common.DbConnection> 对象：适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbConnection> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlConnection> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcConnection> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleConnection> 对象。  
  
## <a name="in-this-section"></a>本节内容  
 [建立连接](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 介绍如何使用**连接**对象建立与数据源的连接。  
  
 [连接事件](../../../../docs/framework/data/adonet/connection-events.md)  
 介绍如何使用**InfoMessage**事件从数据源中检索信息性消息。  
  
## <a name="see-also"></a>请参阅

- [连接字符串](../../../../docs/framework/data/adonet/connection-strings.md)
- [连接池](../../../../docs/framework/data/adonet/connection-pooling.md)
- [命令和参数](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [事务和并发性](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
