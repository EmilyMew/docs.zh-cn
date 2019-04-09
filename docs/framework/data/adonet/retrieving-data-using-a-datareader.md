---
title: 使用 DataReader 检索 ADO 数据
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 8063f239123ec1a2f2650adf9d76f7ceaaa50673
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128673"
---
# <a name="retrieve-data-using-a-datareader"></a>使用 DataReader 检索数据
若要检索的数据使用**DataReader**，创建的实例**命令**对象，并创建**DataReader**通过调用**Command.ExecuteReader**从数据源中检索行。 **DataReader**提供未缓冲的数据流使过程逻辑可以有效地按顺序处理数据源的结果的数据。 **DataReader**时要检索的数据量大，因为这些数据不在内存中缓存是一个不错的选择。

下面的示例演示如何使用**DataReader**，其中`reader`表示有效的 DataReader 和`command`表示有效的命令对象。  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

使用**DataReader.Read**方法从查询结果中获取某一行。 可以通过传递的名称或序号的列访问每个列返回行**DataReader**。 但是，为了获得最佳性能， **DataReader**提供了一系列的方法，可用于访问本机数据类型中的列值 (**GetDateTime**， **GetDouble**， **GetGuid**， **GetInt32**，依此类推)。 有关数据提供程序特定的类型化取值函数方法的列表**Datareader**，请参阅<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。 使用类型化取值函数方法，当您知道基础数据类型可减少检索列值时所需的类型转换量。  
  
 下面的示例循环访问**DataReader**对象并从每个行返回两个列。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>关闭 DataReader  
 始终调用**关闭**方法时使用完**DataReader**对象。  
  
 如果你**命令**包含输出参数或返回值，这些值不是后才可**DataReader**已关闭。  
  
 虽然**DataReader**处于打开状态，**连接**处于独占方式使用**DataReader**。 不能执行任何命令**连接**，包括创建另一个**DataReader**，直到原始**DataReader**已关闭。  
  
> [!NOTE]
>  不要调用**关闭**或**Dispose**上**连接**即**DataReader**，或在任何其他托管的对象**Finalize**类的方法。 在终结器中，仅释放类直接拥有的非托管资源。 如果您的类不拥有任何非托管的资源，不包括**Finalize**在类定义中的方法。 有关详细信息，请参阅[垃圾回收](../../../../docs/standard/garbage-collection/index.md)。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>使用 NextResult 检索多个结果集  
 如果**DataReader**返回多个结果集，调用**NextResult**方法来循环访问结果按顺序设置。 以下示例显示 <xref:System.Data.SqlClient.SqlDataReader> 如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法处理两个 SELECT 语句的结果。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>从 DataReader 中获取架构信息  
 虽然**DataReader**是打开状态，可以检索有关当前结果集使用的架构信息**GetSchemaTable**方法。 **GetSchemaTable**返回<xref:System.Data.DataTable>包含行和列包含当前结果集的架构信息填充的对象。 **DataTable**结果集的每一列中对应一行。 架构表的每个列都映射到属性中返回的列的结果的行设置，其中**ColumnName**属性名称和列的值是属性的值。 下面的示例写出的架构信息**DataReader**。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>使用 OLE DB 章节  
 分层行集或章节 (OLE DB 类型**DBTYPE_HCHAPTER**，ADO 类型**adChapter**)，可以使用检索<xref:System.Data.OleDb.OleDbDataReader>。 当包含某章节的查询返回作为**DataReader**，一章中列的形式返回**DataReader** ，并作为公开**DataReader**对象。  
  
 ADO.NET**数据集**还可用于通过使用表之间的父-子关系，表示分层行集。 有关详细信息，请参阅[数据集、 数据表和数据视图](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。  
  
 以下代码示例使用 MSDataShape 提供程序来为客户列表中的每个客户生成订单的章节列。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>使用 Oracle REF Cursor 返回结果  
 Oracle .NET Framework 数据提供程序支持使用 Oracle REF CURSOR 返回查询结果。 Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 的形式返回。  
  
 可以检索<xref:System.Data.OracleClient.OracleDataReader>对象，表示通过使用 Oracle REF CURSOR<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法。 此外可以指定<xref:System.Data.OracleClient.OracleCommand>返回一个或多个 Oracle REF Cursor 作为**SelectCommand**有关<xref:System.Data.OracleClient.OracleDataAdapter>用来填充<xref:System.Data.DataSet>。  
  
 若要访问从 Oracle 数据源返回的 REF CURSOR，创建<xref:System.Data.OracleClient.OracleCommand>为您的查询，并添加引用到 REF CURSOR 的输出参数<xref:System.Data.OracleClient.OracleCommand.Parameters>的集合在<xref:System.Data.OracleClient.OracleCommand>。 该参数的名称必须与查询中的 REF CURSOR 参数名称相匹配。 参数的类型设置<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>。 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法将<xref:System.Data.OracleClient.OracleCommand>返回<xref:System.Data.OracleClient.OracleDataReader>的 REF CURSOR。  
  
 如果你<xref:System.Data.OracleClient.OracleCommand>返回多个 REF CURSOR，添加多个输出参数。 可以通过调用访问不同的 REF Cursor<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法。 在调用<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>返回<xref:System.Data.OracleClient.OracleDataReader>引用第一个 REF CURSOR。 然后，可以调用<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>方法访问随后的 REF Cursor。 尽管中的参数在<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合匹配 REF CURSOR 输出参数的名称，<xref:System.Data.OracleClient.OracleDataReader>添加到中的顺序访问这些<xref:System.Data.OracleClient.OracleCommand.Parameters>集合。  
  
 例如，请看下面这个 Oracle 包和包正文。  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 下面的代码创建<xref:System.Data.OracleClient.OracleCommand>类型的两个参数添加从先前的 Oracle 包返回 REF Cursor<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>到<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合。  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 以下代码将返回上一个命令使用的结果<xref:System.Data.OracleClient.OracleDataReader.Read>并<xref:System.Data.OracleClient.OracleDataReader.NextResult>方法的<xref:System.Data.OracleClient.OracleDataReader>。 REF CURSOR 参数按顺序返回。  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 下面的示例使用前一命令来填充<xref:System.Data.DataSet>与 Oracle 包的结果。  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
>  若要避免**OverflowException**，我们建议你还处理任何从 Oracle NUMBER 类型转换为有效的.NET Framework 类型存储中的值之前<xref:System.Data.DataRow>。 可以使用<xref:System.Data.Common.DataAdapter.FillError>事件来确定是否**OverflowException**已发生。 有关详细信息<xref:System.Data.Common.DataAdapter.FillError>事件，请参阅[处理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
## <a name="see-also"></a>请参阅

- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [命令和参数](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [检索数据库架构信息](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
