---
title: ADO.NET 中的并行执行
ms.date: 03/30/2017
ms.assetid: 9f9ba96d-9f89-4f65-bb2f-6860879f4393
ms.openlocfilehash: a8747d749ed7e751ba577a2cd29c2048065f2645
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136755"
---
# <a name="side-by-side-execution-in-adonet"></a>ADO.NET 中的并行执行
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中的并行执行是指在安装了 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的多个版本的计算机上以独占方式使用编译的应用程序所针对的版本执行该应用程序的能力。 有关配置通过并行执行的详细信息，请参阅[-并行执行](../../../../docs/framework/deployment/side-by-side-execution.md)。  
  
 使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的某个版本编译的应用程序可以在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的其他版本上运行。 不过，建议您为安装的每个 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 版本都编译一个相应版本的应用程序，并单独运行这些应用程序。 在任一方案中，您都应该知道各版本之间 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中的更改，这些更改可能影响应用程序的向前或向后兼容性。  
  
## <a name="forward-compatibility-and-backward-compatibility"></a>向前兼容性和向后兼容性  
 向前兼容性表示应用程序可以使用较早版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 进行编译，但是仍可以在较高版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 上成功运行。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 为编写的代码[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.1 版是与更高版本向前兼容。  
  
 向后兼容性表示应用程序为较高版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 编译，但可以继续在较早版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 上运行而不丧失任何功能。 当然，这不包括新版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中引入的功能。  
  
## <a name="the-net-framework-data-provider-for-odbc"></a>ODBC .NET Framework 数据提供程序  
 从 1.1 版开始，适用于 ODBC 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序 (<xref:System.Data.Odbc>) 作为 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的一部分提供。 ODBC 数据提供程序可供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版 Web 开发人员从下载[数据访问和存储开发人员中心](https://go.microsoft.com/fwlink/?linkid=4173)。 下载的命名空间[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ODBC 数据提供程序是**Microsoft.Data.Odbc**。  
  
 如果必须开发的应用程序[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版程序使用 ODBC 数据提供程序连接到您的数据源，并且您想要运行该应用程序[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.1 版或更高版本，则必须将 odbc 更新命名空间数据访问接口与**System.Data.Odbc**。 然后，您必须针对 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的较新版本重新编译该应用程序。  
  
 如果您有一个针对 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版（或更高版本）开发的应用程序，该应用程序使用 ODBC 数据提供程序连接到您的数据源，并且您想要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版上运行该应用程序，则必须下载相应的 ODBC 数据提供程序并将其安装在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版的系统上。 然后必须更改到 ODBC 数据提供程序的命名空间**Microsoft.Data.Odbc**，并重新编译的应用程序[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版。  
  
## <a name="the-net-framework-data-provider-for-oracle"></a>Oracle .NET Framework 数据提供程序  
 从 1.1 版开始，适用于 Oracle 的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序 (<xref:System.Data.OracleClient>) 作为 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的一部分提供。 数据提供程序可供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版 Web 开发人员从下载[数据访问和存储开发人员中心](https://go.microsoft.com/fwlink/?linkid=4173)。  
  
 如果您有一个针对 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版（或更高版本）开发的应用程序，该应用程序使用数据提供程序连接到您的数据源，并且您想要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版上运行该应用程序，则必须下载相应的数据提供程序并将其安装在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版的系统上。  
  
## <a name="code-access-security"></a>代码访问安全性  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序（<xref:System.Data.SqlClient>、<xref:System.Data.OleDb>）必需具有 FullTrust 权限才能运行。 在权限级别低于 FullTrust 的区域中，从 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序的任何尝试都会导致 <xref:System.Security.SecurityException>。  
  
 但从 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版开始，所有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序均可以在部分信任的区域中使用。 此外，还向 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 数据提供程序添加了一项新的安全功能。 通过该功能可以限制特定安全区域中可以使用的连接字符串。 您也可以对特定安全区域禁用空白密码。 有关更多信息，请参见 [Code Access Security and ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)。  
  
 因为每个 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 安装均有独立的 Security.config 文件，所以安全设置不存在兼容性问题。 不过，如果应用程序依赖于 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 1.1 版以及更高版本中包含的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的附加安全功能，则将无法将该应用程序发布到 1.0 版系统中。  
  
## <a name="sqlcommand-execution"></a>SqlCommand 执行  
 从 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版开始，更改了 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 在数据源中执行命令的方式。  
  
 在中[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.0 版中，<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>的上下文中执行的所有命令**sp_executesql**存储过程。 因此，影响连接状态的命令（例如，SET NOCOUNT ON）只应用于当前命令的执行。 对于在连接打开时执行的任何后续命令，连接状态不会被修改。  
  
 在中[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]1.1 版以及更高版本，版本<xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>仅的上下文中执行的命令**sp_executesql**存储过程，当命令含有参数，从而提高性能。 因此，如果非参数化命令中包含影响连接状态的命令，会修改在连接打开时执行的所有后续命令的连接状态。  
  
 请考虑下面这个在 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 调用中执行的批命令。  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
```  
  
 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版以及更高版本中，NOCOUNT 对连接打开时执行的任何后续命令都将保持为 ON。 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中，NOCOUNT 只在执行当前命令时为 ON。  
  
 如果您的应用程序依赖于任一 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 版本的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的行为，则这一更改会影响应用程序的向前和向后兼容性。  
  
 对于在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的早期版本和更高版本上运行的应用程序，可以编写代码以确保不管在其上运行应用程序的系统的版本如何，应用程序的行为始终相同。 如果要确保某个命令修改所有后续命令的连接状态，建议您使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 来执行该命令。 如果要确保某个命令不修改所有后续命令的连接，建议您在命令中包括用于重置连接状态的命令。 例如：  
  
```sql
SET NOCOUNT ON;  
SELECT * FROM dbo.Customers;  
SET NOCOUNT OFF;  
```  
  
## <a name="see-also"></a>请参阅

- [ADO.NET 概述](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
