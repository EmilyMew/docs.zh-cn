---
title: 如何：更新数据库中的行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 84ef85b1e53d97ff468c3360af5e394a0e4ad776
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091187"
---
# <a name="how-to-update-rows-in-the-database"></a>如何：更新数据库中的行
可以通过修改与关联的对象的成员值来更新数据库中的行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Table%601>集合，然后将更改提交到数据库。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 将转换成相应的 SQL 所做的更改`UPDATE`命令。  
  
> [!NOTE]
>  您可以重写 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert` 和 `Update` 数据库操作的 `Delete` 默认方法。 有关详细信息，请参阅[自定义插入、 更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。  
>   
>  使用 Visual Studio 的开发人员可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]来开发用于同一目的的存储的过程。  
  
 以下步骤假定您已通过有效的 <xref:System.Data.Linq.DataContext> 连接到 Northwind 数据库。 有关详细信息，请参阅[如何：连接到数据库](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。  
  
### <a name="to-update-a-row-in-the-database"></a>更新数据库中的行  
  
1.  查询数据库中要更新的行。  
  
2.  对得到的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象中的成员值进行所需的更改。  
  
3.  将更改提交到数据库。  
  
## <a name="example"></a>示例  
 下面的示例查询数据库中编号为 11000 的订单，然后更改所得到的 `ShipName` 对象中的 `ShipVia` 和 `Order` 值。 最后，对这些成员值的更改将作为对 `ShipName` 和 `ShipVia` 列的更改提交到数据库。  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [如何：管理更改冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [进行和提交数据更改](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
