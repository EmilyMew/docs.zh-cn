---
title: SQL Server 中的批量复制操作
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194794"
---
# <a name="bulk-copy-operations-in-sql-server"></a>SQL Server 中的批量复制操作
Microsoft SQL Server 包含名为的常用命令行实用工具**bcp**的快速大容量复制大型文件到表或视图中的 SQL Server 数据库。 使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类可以编写提供类似功能的托管代码解决方案。 还可以通过其他方式将数据加载到 SQL Server 表中（例如 INSERT 语句），但是 <xref:System.Data.SqlClient.SqlBulkCopy> 提供的性能要明显优于这些方式。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> 类只能用于向 SQL Server 表中写入数据。 但是，数据源不限于 SQL Server；可以使用任何数据源，只要数据可以加载到 <xref:System.Data.DataTable> 实例或使用 <xref:System.Data.IDataReader> 实例读取即可。  
  
 使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类可以执行下列操作：  
  
-   单次批量复制操作  
  
-   多次批量复制操作  
  
-   事务中的批量复制操作  
  
> [!NOTE]
>  使用.NET Framework 1.1 或更早版本时 (不支持<xref:System.Data.SqlClient.SqlBulkCopy>类)，可以执行 SQL Server TRANSACT-SQL **BULK INSERT**语句使用<xref:System.Data.SqlClient.SqlCommand>对象。  
  
## <a name="in-this-section"></a>本节内容  
 [批量复制示例设置](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 描述批量复制示例中使用的表，并提供用于在 AdventureWorks 数据库中创建表的 SQL 脚本。  
  
 [单个批量复制操作](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类将数据单次批量复制到 SQL Server 实例中，以及如何使用 Transact-SQL 语句和 <xref:System.Data.SqlClient.SqlCommand> 类执行批量复制操作。  
  
 [多个批量复制操作](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 描述如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类将数据多次批量复制到 SQL Server 实例中。  
  
 [事务和批量复制操作](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 描述如何在事务中执行批量复制操作，包括如何提交或回滚事务。  
  
## <a name="see-also"></a>请参阅

- [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
