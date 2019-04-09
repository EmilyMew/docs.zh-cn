---
title: 复制数据集内容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: cb2a172ac4e6a0ce4852f4c7cf7044583d9ab6c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077754"
---
# <a name="copying-dataset-contents"></a>复制数据集内容
可以创建一份<xref:System.Data.DataSet>，以便可以处理的数据，而不会影响原始数据，或处理中的数据的子集**数据集**。 复制时**数据集**，你可以：  
  
-   创建的一个精确副本**数据集**，包括架构、 数据、 行状态信息和行版本。  
  
-   创建**数据集**，其中包含对现有的架构**数据集**，但已被修改的行。 可以返回已修改的所有行，也可以指定特定**DataRowState**。 有关行状态的详细信息，请参阅[行状态和行版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
-   复制的架构，即关系结构**数据集**仅，而不复制任何行。 可以使用 <xref:System.Data.DataTable> 将行导入现有 <xref:System.Data.DataTable.ImportRow%2A>。  
  
 若要创建的一个精确副本**数据集**其中包括架构和数据，请使用<xref:System.Data.DataSet.Copy%2A>方法**数据集**。 下面的代码示例演示如何创建完全相同的副本**数据集**。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 若要创建一份**数据集**其中包括架构和仅数据表示**Added**， **Modified**，或**已删除**行，请使用<xref:System.Data.DataSet.GetChanges%2A>方法**数据集**。 此外可以使用**GetChanges**返回只有指定的行状态的行通过传递**DataRowState**值时调用**GetChanges**。 下面的代码示例演示如何传递**DataRowState**调用时**GetChanges**。  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 若要创建一份**数据集**仅包含架构，请使用<xref:System.Data.DataSet.Clone%2A>方法**数据集**。 此外可以将现有行添加到克隆**数据集**使用**ImportRow**方法**DataTable**。 **ImportRow**将数据、 行状态和行版本信息添加到指定的表。 只有当列名称匹配且数据类型兼容时，才会添加列值。  
  
 下面的代码示例创建的克隆**数据集**然后将行添加从原始**数据集**到**客户**表中**数据集**克隆客户位置**国家 （地区)** 列具有"Germany"的值。  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
