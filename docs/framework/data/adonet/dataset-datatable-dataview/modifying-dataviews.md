---
title: 修改 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 6e340b9b72735598650d2eefa6e19ab40fffc2e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111548"
---
# <a name="modifying-dataviews"></a>修改 DataView
可以使用 <xref:System.Data.DataView> 在基础表中添加、删除或修改数据行。 若要使用的功能**DataView**若要修改基础表中的数据由设置其中一个的三个布尔属性控制**DataView**。 这三个属性是 <xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> 和 <xref:System.Data.DataView.AllowDelete%2A>。 它们设 **，则返回 true**默认情况下。  
  
 如果**AllowNew**是**true**，可以使用<xref:System.Data.DataView.AddNew%2A>方法**DataView**若要创建一个新<xref:System.Data.DataRowView>。 请注意，新行不会实际添加到基础<xref:System.Data.DataTable>直到<xref:System.Data.DataRowView.EndEdit%2A>方法**DataRowView**调用。 如果<xref:System.Data.DataRowView.CancelEdit%2A>方法**DataRowView**是调用，会丢弃新行。 您可以编辑只有一个另请注意**DataRowView**一次。 如果您调用**AddNew**或**BeginEdit**方法**DataRowView**存在挂起行，而**EndEdit**对隐式调用挂起的行。 当**EndEdit**是调用，所做的更改会应用于基础**DataTable**和更高版本可以是提交或拒绝使用**AcceptChanges**或**RejectChanges**的方法**DataTable**，**数据集**，或**DataRow**对象。 如果**AllowNew**是**false**，如果调用引发异常**AddNew**方法**DataRowView**。  
  
 如果**AllowEdit**是**true**，可以修改的内容**DataRow**通过**DataRowView**。 你可以确认对基础行使用的更改**DataRowView.EndEdit**或拒绝所做的更改使用**DataRowView.CancelEdit**。 注意，一次只能编辑一行。 如果您调用**AddNew**或**BeginEdit**方法**DataRowView**存在挂起行，而**EndEdit**对隐式调用挂起的行。 当**EndEdit**调用时，建议的更改都将置于**当前**行版本的基础**DataRow**和更高版本可以是提交或拒绝使用**AcceptChanges**或**RejectChanges**的方法**DataTable**，**数据集**，或**DataRow**对象。 如果**AllowEdit**是**false**，如果你试图修改中的值引发异常**DataView**。  
  
 当现有**DataRowView**正在编辑的基础事件**DataTable**仍将引发具有建议的更改。 请注意，如果您调用**EndEdit**或**CancelEdit**对基础**DataRow**、 挂起的更改将应用或取消而不管是否**EndEdit**或**CancelEdit**上调用**DataRowView**。  
  
 如果**AllowDelete**是**true**，您可以从中删除行**DataView**通过**删除**方法**DataView**或**DataRowView**对象和的行删除从基础**DataTable**。 您可以更高版本提交或拒绝使用删除**AcceptChanges**或**RejectChanges**分别。 如果**AllowDelete**是**false**，如果调用引发异常**删除**方法**DataView**或**DataRowView**。  
  
 下面的代码示例禁用通过**DataView**到删除行，并将新行添加到基础表使用**DataView**。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
