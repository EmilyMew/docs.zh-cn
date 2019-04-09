---
title: 在 ADO.NET 中修改大值 (max) 数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 417afd5f614aee8db0aeec2377973ad894e04384
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119296"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>在 ADO.NET 中修改大值 (max) 数据
大型对象 (LOB) 数据类型是那些超过 8 千字节 (KB) 最大行大小的数据类型。 SQL Server 为 `max`、`varchar` 和 `nvarchar` 数据类型提供了 `varbinary` 说明符以允许存储最大为 2^32 字节的值。 表列和 Transact-SQL 变量可以指定 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 数据类型。 在 ADO.NET 中，`max` 数据类型可通过 `DataReader` 来提取，并可指定为输入和输出参数值而无需任何特殊处理。 对于大型 `varchar` 数据类型，可以增量检索和更新数据。  
  
 可以使用 `max` 数据类型进行比较（作为 Transact-SQL 变量）和进行串联。 它们还可以用于 SELECT 语句的 DISTINCT、ORDER BY、GROUP BY 子句中，以及用于聚合、联接和子查询中。  
  
 下表提供指向 SQL Server 联机丛书中的文档的链接。  
  
 **SQL Server 联机丛书**  
  
1.  [使用大值数据类型](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>大值类型限制  
 下面的限制适用于 `max` 数据类型，但对于较小的数据类型则不存在此限制：  
  
-   `sql_variant` 不能包含大型 `varchar` 数据类型。  
  
-   大型 `varchar` 列不能指定为索引中的键列。 它们可以存在于非聚集索引中包含的列中。  
  
-   大型 `varchar` 列不能用作分区键列。  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>在 Transact-SQL 中使用大值类型  
 Transact-SQL `OPENROWSET` 函数是一个用于连接和访问远程数据的一次性方法。 它包含从 OLE DB 数据源访问远程数据所需的所有连接信息。 `OPENROWSET` 可以引用一个查询的 FROM 子句中像表名称。 根据 OLE DB 提供程序的功能，它还可作为 INSERT、UPDATE 或 DELETE 语句的目标表被引用。  
  
 `OPENROWSET` 功能包含 `BULK` 行集提供程序，通过此提供程序，您可以直接从文件读取数据而不必将数据加载到目标表 这使您可以在简单的 INSERT SELECT 语句中使用 `OPENROWSET`。  
  
 `OPENROWSET BULK`选项参数有效地控制在何处开始和结束读取数据、 如何处理错误，以及如何解释数据。 例如，可以指定将数据文件作为 `varbinary`、`varchar` 或 `nvarchar` 类型的单行单列行集合进行读取。 有关完整语法和选项，请参见 SQL Server 联机图书。  
  
 下面的示例将一幅照片插入 AdventureWorks 示例数据库的 ProductPhoto 表中。 当使用`BULK OPENROWSET`提供程序，也必须提供甚至列的命名的列表不将值插入到每个列。 在本例中，主键定义为标识列，并可从列的列表中省略。 请注意，您还必须在 `OPENROWSET` 语句的末尾提供一个相关名称，在本例中该名称是 ThumbnailPhoto。 该名称与文件要加载到的 `ProductPhoto` 表中的列关联。  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>使用 UPDATE .WRITE 更新数据  
 Transact-SQL UPDATE 语句具有新的 WRITE 语法，用于修改 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 列的内容。 它允许您对数据执行部分更新。 此处所示的 UPDATE .WRITE 语法为缩写形式：  
  
 更新  
  
 { *\<object>* }  
  
 SET  
  
 { *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }  
  
 WRITE 方法指定的值的一部分*column_name*将进行相应修改。 表达式是将复制到的值*column_name*，则`@Offset`是从该处将写入表达式的开始点和`@Length`参数是列中的该部分的长度。  
  
|如果|Then|  
|--------|----------|  
|表达式设置为 NULL|`@Length` 将忽略和中的值*column_name*会被截断处指定`@Offset`。|  
|`@Offset` 为 NULL|更新操作将表达式的现有末尾追加*column_name*值和`@Length`将被忽略。|  
|`@Offset` 大于 column_name 值的长度|SQL Server 返回一个错误。|  
|`@Length` 为 NULL|更新操作移除从 `@Offset` 到 `column_name` 值末尾的所有数据。|  
  
> [!NOTE]
>  `@Offset` 和 `@Length` 都不能是负数。  
  
## <a name="example"></a>示例  
 此 Transact-SQL 示例更新 DocumentSummary（AdventureWorks 数据库的 Document 表中的 `nvarchar(max)` 列）中的部分值。 通过指定替换单词、现有数据中要替换的单词的开始位置（偏移量）以及要替换的字符数（长度），单词“components”将被替换为“features”。 该示例在 UPDATE 语句之前和之后都包含 SELECT 语句以便比较结果。  
  
```  
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>在 ADO.NET 中使用大值类型  
 可以使用大值类型在 ADO.NET 中通过指定大值类型作为<xref:System.Data.SqlClient.SqlParameter>中的对象<xref:System.Data.SqlClient.SqlDataReader>以返回结果集，或者通过使用<xref:System.Data.SqlClient.SqlDataAdapter>填充`DataSet` / `DataTable`。 使用大值类型的方式和使用其相关的较小值数据类型的方式之间没有什么不同。  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>使用 GetSqlBytes 检索数据  
 `GetSqlBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用于检索 `varbinary(max)` 列的内容。 下面的代码段假定一个名为 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 对象（该对象可从表中选择 `varbinary(max)` 数据）和一个名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象（该对象可将该数据检索为 <xref:System.Data.SqlTypes.SqlBytes>）。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>使用 GetSqlChars 检索数据  
 `GetSqlChars` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用于检索 `varchar(max)` 或 `nvarchar(max)` 列的内容。 下面的代码段假定一个名为 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 对象（该对象可从表中选择 `nvarchar(max)` 数据）和一个名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象（该对象可检索该数据）。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>使用 GetSqlBinary 检索数据  
 `GetSqlBinary` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用于检索 `varbinary(max)` 列的内容。 下面的代码段假定一个名为 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 对象（该对象可从表中选择 `varbinary(max)` 数据）和一个名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象（该对象可将该数据检索为 <xref:System.Data.SqlTypes.SqlBinary> 流）。  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>使用 GetBytes 检索数据  
 `GetBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法将从指定列偏移量开始的字节流读入到数组中从指定数组偏移量开始的位置。 下面的代码段假定一个名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象，该对象可将字节检索到字节数组中。 请注意，与 `GetSqlBytes` 不同，`GetBytes` 要求指定数组缓冲区的大小。  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>使用 GetValue 检索数据  
 `GetValue` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法将指定列偏移量处的值读入数组。 下面的代码段假定一个名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象，该对象检索第一个列偏移量处的二进制数据，然后检索第二个列偏移量处的字符串数据。  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>从大值类型转换为 CLR 类型  
 可以使用任何字符串转换方法（例如 `varchar(max)`）来转换 `nvarchar(max)` 或 `ToString` 列的内容。 下面的代码段假定一个可检索数据的名为 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 对象。  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>示例  
 下面的代码检索 `LargePhoto` 数据库的 `ProductPhoto` 表中的名称和 `AdventureWorks` 对象，并将其保存到文件。 编译程序集时需要引用 <xref:System.Drawing> 命名空间。  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法返回一个 <xref:System.Data.SqlTypes.SqlBytes> 对象，该对象公开 `Stream` 属性。 代码使用此创建新`Bitmap`对象，并将其保存在 Gif `ImageFormat`。  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>使用大值类型参数  
 在 <xref:System.Data.SqlClient.SqlParameter> 对象中使用大型值类型的方法与在 <xref:System.Data.SqlClient.SqlParameter> 对象中使用较小值类型的方法相同。 您可以检索大值类型作为<xref:System.Data.SqlClient.SqlParameter>值，如下面的示例中所示。 代码假定在 AdventureWorks 示例数据库中存在以下 GetDocumentSummary 存储过程。 存储的过程将一个名为的输入的参数@DocumentID，并返回 DocumentSummary 列中的内容@DocumentSummary输出参数。  
  
```  
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>示例  
 ADO.NET 代码创建 <xref:System.Data.SqlClient.SqlConnection> 和 <xref:System.Data.SqlClient.SqlCommand> 对象，以执行 GetDocumentSummary 存储过程并检索以大值类型存储的文档摘要。 代码将值传递@DocumentID输入参数，并显示结果传递回@DocumentSummary输出控制台窗口中的参数。  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [SQL Server 二进制和大值数据](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [SQL Server 数据类型映射](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [ADO.NET 中的 SQL Server 数据操作](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
