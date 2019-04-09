---
title: 在 DataView 中查询 DataRowView 集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 8b6b6c5b9d7157b1279f23770b1d223635252685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092950"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>在 DataView 中查询 DataRowView 集合
<xref:System.Data.DataView> 公开了 <xref:System.Data.DataRowView> 对象的可枚举集合。 <xref:System.Data.DataRowView> 表示自定义的视图<xref:System.Data.DataRow>，并显示特定版本的<xref:System.Data.DataRow>在控件中。 只有一种版本的 <xref:System.Data.DataRow> 可通过控件显示，例如 <xref:System.Windows.Forms.DataGridView>。 您可以通过 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRowView> 属性访问 <xref:System.Data.DataRowView.Row%2A> 公开的 <xref:System.Data.DataRowView>。 当使用 <xref:System.Data.DataRowView> 查看值时，<xref:System.Data.DataView.RowStateFilter%2A> 属性决定公开基础 <xref:System.Data.DataRow> 的哪个行版本。 有关访问使用不同的行版本信息<xref:System.Data.DataRow>，请参阅[行状态和行版本](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。 因为 <xref:System.Data.DataRowView> 公开的 <xref:System.Data.DataView> 对象的集合是可枚举的，所以您可以使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 对它执行查询。  
  
 下面的示例对 `Product` 表执行查询查找红色的产品，并从该查询创建表。 从该表创建 <xref:System.Data.DataView> 并将 <xref:System.Data.DataView.RowStateFilter%2A> 属性设置为筛选已删除和修改的行。 然后将 <xref:System.Data.DataView> 用作 LINQ 查询中的源，并将已修改和删除的 <xref:System.Data.DataRowView> 对象绑定到 <xref:System.Windows.Forms.DataGridView> 控件。  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 下面的示例从绑定到 <xref:System.Windows.Forms.DataGridView> 控件的视图创建了一个产品表。 对 <xref:System.Data.DataView> 进行查询查找红色的产品，并将排序的结果绑定到 <xref:System.Windows.Forms.DataGridView> 控件。  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>请参阅

- [数据绑定和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
