---
title: 创建数据表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 272976d3c581d3e8a5860ba5cf3f9695ca370d8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112380"
---
# <a name="creating-a-datatable"></a>创建数据表
<xref:System.Data.DataTable> 表示一个内存内关系数据的表，可以独立创建和使用，也可以由其他 .NET Framework 对象使用，最常见的情况是作为 <xref:System.Data.DataSet> 的成员使用。  
  
 您可以创建**DataTable**通过使用相应的对象**DataTable**构造函数。 您可以将其添加到**数据集**通过使用**添加**方法以将其添加到**DataTable**对象的**表**集合。  
  
 此外可以创建**DataTable**对象内**数据集**通过**填充**或**FillSchema**方法**DataAdapter**对象，或从预定义或推断 XML 架构使用**ReadXml**， **ReadXmlSchema**，或**InferXmlSchema**方法**数据集**。 请注意，添加之后**DataTable**作为的成员**表**之一集合**数据集**，不能将其添加到的任何其他表集合**数据集**。  
  
 当你首次创建**DataTable**，它没有架构 （即结构）。 若要定义的表的架构，必须创建并添加<xref:System.Data.DataColumn>对象添加到**列**表的集合。 此外可以定义表的主键列和创建并添加**约束**对象添加到**约束**表的集合。 定义的架构后**DataTable**，可以通过添加到表中添加数据行**DataRow**对象添加到**行**表的集合。  
  
 不要求您提供的值<xref:System.Data.DataTable.TableName%2A>属性在创建时**DataTable**; 可以在另一个时，指定该属性或者可以将其留空。 但是，您添加的表，而无需**TableName**值设置为**数据集**，该表会得到表的递增的默认名称*N*，从开始 Table0"表"。  
  
> [!NOTE]
>  我们建议你避免"表*N*"命名约定，在提供时**TableName**值，因为所提供的名称可能与中现有的默认表名称冲突**数据集**. 如果提供的名称已经存在，将引发异常。  
  
 下面的示例创建的实例**DataTable**对象，并将其分配名称"Customers。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 下面的示例创建的实例**DataTable**通过将其添加到**表**的集合**数据集**。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [从 DataAdapter 填充数据集](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [从 XML 加载数据集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [从 XML 加载数据集架构信息](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
