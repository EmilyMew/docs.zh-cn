---
title: SqlClient 中的已知问题（实体框架）
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: a3df5a42b40e1851875c35165301af082f5d3269
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073801"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>SqlClient 中的已知问题（实体框架）
本节介绍与 SQL Server .NET Framework 数据提供程序 (SqlClient) 有关的已知问题。  
  
## <a name="trailing-spaces-in-string-functions"></a>字符串函数中的尾随空格  
 SQL Server 将忽略字符串值中的尾随空格。 因此，传递字符串中的尾随空格可能导致不可预知的结果，甚至会导致失败。  
  
 如果您必须具有在字符串中的尾随空格，您应考虑追加在结束时，使用空白字符，以便 SQL Server 不会修整字符串。 如果尾随空格不是必需的，应在传递给查询管道之前进行修整。  
  
## <a name="right-function"></a>RIGHT 函数  
 如果将非 `null` 值和 0 分别作为第一个自变量和第二个自变量传递给 `RIGHT(nvarchar(max)`, 0`)` 或 `RIGHT(varchar(max)`, 0`)`，将返回 `NULL` 值，而不是 `empty` 字符串。  
  
## <a name="cross-and-outer-apply-operators"></a>CROSS 和 OUTER APPLY 运算符  
 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 引入了 CROSS 和 OUTER APPLY 运算符。 在某些情况下查询管道可能生成包含 CROSS APPLY 和/或 OUTER APPLY 运算符的 TRANSACT-SQL 语句。 因为某些后端提供程序，包括 SQL Server 的版本早于[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]、 不支持这些运算符，不能对这些后端提供程序执行此类查询。  
  
 下面是一些可能导致输出查询中出现 CROSS APPLY 和/或 OUTER APPLY 运算符的典型情况：  
  
-   带分页的相关子查询。  
  
-   相关子查询或导航所生成的集合上的 `AnyElement`。  
  
-   使用接受元素选择器的分组方法的 LINQ 查询。  
  
-   显式指定了 CROSS APPLY 或 OUTER APPLY 的查询  
  
-   在 REF 构造上具有 DEREF 构造的查询。  
  
## <a name="skip-operator"></a>SKIP 运算符  
 如果使用的是 [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]，则对非键列同时使用 SKIP 和 ORDER BY 可能会返回不正确的结果。 如果非键列中有重复数据，那么跳过的行数可能多于指定的行数。 这是由于 [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]对 SKIP 的解释方式造成的。 例如，在下面的查询中，如果 `E.NonKeyColumn` 有重复值，则跳过的行可能超过 5 行：  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>以正确的 SQL Server 版本为目标  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]目标[!INCLUDE[tsql](../../../../../includes/tsql-md.md)]查询中指定的 SQL Server 版本上基于`ProviderManifestToken`存储模型 (.ssdl) 文件中的架构元素的属性。 您实际连接到的 SQL Server 的版本可能不是这一版本。 例如，如果您使用的是 SQL Server 2005，但 `ProviderManifestToken` 特性设置为 2008，则可能无法在服务器上执行生成的 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 查询。 例如，在 SQL Server 的早期版本上，无法执行使用了 SQL Server 2008 所引入的新日期时间类型的查询。 如果您使用的是 SQL Server 2005，但 `ProviderManifestToken` 属性设置为 2000，则生成的 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 查询可能不是最佳的，您也可能收到指出该查询不受支持的异常消息。 有关详细信息，请参阅 CROSS 和 OUTER APPLY 运算符前面的部分，本主题。  
  
 某些数据库行为取决于为数据库设置的兼容级别。 如果 `ProviderManifestToken` 属性设置为 2005 并且 SQL Server 版本为 2005，但数据库的兼容级别设置为“80”(SQL Server 2000)，则生成的 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 将以 SQL Server 2005 为目标，但可能会因兼容级别设置而无法正常执行。 例如，如果 ORDER BY 列表中的列名与选择器中的列名相同，则可能会丢失排序信息。  
  
## <a name="nested-queries-in-projection"></a>投影中的嵌套查询  
 投影子句中的嵌套查询可在服务器上转换为笛卡尔积查询。 在某些后端服务器，包括 SLQ Server，这会导致 TempDB 表变得非常庞大。 这样会降低服务器性能。  
  
 下面是投影子句中嵌套查询的示例：  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>服务器生成的 GUID 标识值  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支持服务器生成的 GUID 类型标识值，但提供程序必须支持在插入行后返回服务器生成的标识值。 从 SQL Server 2005 开始，你可以通过 SQL Server 数据库中返回服务器生成的 GUID 类型[OUTPUT 子句](https://go.microsoft.com/fwlink/?LinkId=169400)。  
  
## <a name="see-also"></a>请参阅

- [用于实体框架的 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
- [LINQ to Entities 中的已知问题和注意事项](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
