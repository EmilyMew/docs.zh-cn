---
title: 创建数据视图
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 05122f7c980c4b7dfdb27eec73464a4f0556ba99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096675"
---
# <a name="creating-a-dataview"></a>创建数据视图
创建 <xref:System.Data.DataView> 的方法有两种。 可以使用**DataView**构造函数，也可以创建对引用<xref:System.Data.DataTable.DefaultView%2A>属性的<xref:System.Data.DataTable>。 **DataView**构造函数可以为空，或它可以采用**DataTable**为单个参数，或**DataTable**与筛选条件、 排序条件和行状态筛选器。 有关用于与一起使用的其他参数的详细信息**DataView**，请参阅[进行排序和筛选数据](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
 因为的索引**DataView**生成时，均**DataView**创建后，以及时的任何**排序**， **RowFilter**，或**RowStateFilter**属性将被修改，通过提供任何初始排序顺序或筛选条件作为构造函数参数，在创建时获得最佳的性能**DataView**。 创建**DataView**而不指定排序或筛选条件，然后设置**排序**， **RowFilter**，或者**RowStateFilter**属性更高版本使索引生成至少两次： 一旦时**DataView**创建和重新排序或筛选器属性在修改任何。  
  
 请注意，如果您创建**DataView**使用不带任何参数的构造函数，您将无法再使用**DataView**之前已设置**表**属性.  
  
 下面的代码示例演示如何创建**DataView**使用**DataView**构造函数。 一个**RowFilter**，**排序**列中，并且**DataViewRowState**连同提供**DataTable**。  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 下面的代码示例演示如何获取对默认值的引用**DataView**的**DataTable**使用**DefaultView**的表的属性。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [对数据进行排序和筛选](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
