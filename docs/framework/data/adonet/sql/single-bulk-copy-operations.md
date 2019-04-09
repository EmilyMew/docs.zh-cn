---
title: 单个批量复制操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 4fdd578f1537e3521093fd12655a452feaa5a38d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112063"
---
# <a name="single-bulk-copy-operations"></a>单个批量复制操作
执行 SQL Server 批量复制操作最简单的方法就是对数据库执行单次操作。 默认情况下，批量复制操作是作为一个独立的操作执行的：该复制操作以非事务处理方式进行，不可进行回滚。  
  
> [!NOTE]
>  如果需要在出错时回滚批量复制的全部或部分，可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 管理的事务，或在现有事务中执行批量复制操作。 **SqlBulkCopy**也适用于<xref:System.Transactions>如果登记连接 （隐式或显式） 到**System.Transactions**事务。  
>   
>  有关详细信息，请参阅[事务和大容量复制操作](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)。  
  
 执行批量复制操作的一般步骤如下所示：  
  
1.  连接到源服务器上并获取要复制的数据。 如果可以从 <xref:System.Data.IDataReader> 或 <xref:System.Data.DataTable> 对象检索数据，则这些数据还可能来自其他源。  
  
2.  连接到目标服务器 (除非您希望**SqlBulkCopy**来为您建立的连接)。  
  
3.  创建一个 <xref:System.Data.SqlClient.SqlBulkCopy> 对象，设置任何必要的属性。  
  
4.  设置**DestinationTableName**属性以指示目标表用于大容量插入操作。  
  
5.  调用之一**WriteToServer**方法。  
  
6.  还可以更新属性并调用**WriteToServer**根据需要再次。  
  
7.  调用 <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>，或将批量复制操作包装在 `Using` 语句中。  
  
> [!CAUTION]
>  我们建议源列和目标列的数据类型匹配。 如果数据类型不匹配， **SqlBulkCopy**尝试将每个源值转换为目标数据类型，使用采用的规则<xref:System.Data.SqlClient.SqlParameter.Value%2A>。 转换可能会影响性能，还可能会导致意外的错误。 例如，大多数情况下，`Double` 数据类型可以转换为 `Decimal` 数据类型，但是有时就不能。  
  
## <a name="example"></a>示例  
 以下控制台应用程序演示如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 类加载数据。 在此示例中，<xref:System.Data.SqlClient.SqlDataReader>用于复制的数据**Production.Product**表中的 SQL Server **AdventureWorks**到同一个数据库中类似表的数据库。  
  
> [!IMPORTANT]
>  此示例将不运行，除非你已创建的工作表中所述[大容量复制示例设置](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)。 提供此代码演示了使用语法**SqlBulkCopy**仅。 如果源表和目标表位于同一个 SQL Server 实例中，则使用 Transact-SQL `INSERT … SELECT` 语句复制数据会更加容易、更加迅速。  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>使用 Transact-SQL 和命令类执行批量复制操作  
 以下示例说明如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法执行 BULK INSERT 语句。  
  
> [!NOTE]
>  数据源的文件路径相对于服务器。 要成功执行批量复制操作，服务器进程必须具有对该路径的访问权限。  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>请参阅

- [SQL Server 中的批量复制操作](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
