---
title: 如何：通过与数据库值合并解决冲突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 429bca7501bd58440ee894345855141a2a2ed12c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130203"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>如何：通过与数据库值合并解决冲突
若要先对帐预期数据库值与实际数据库值之间的差异，再尝试重新提交更改，则可以使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 将数据库值与当前客户端成员值合并。 有关详细信息，请参阅[开放式并发：概述](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  在所有情况下，都会先通过从数据库中检索更新后的数据来刷新客户端上的记录。 此操作确保了下一次更新尝试将通过相同的并发检查。  
  
## <a name="example"></a>示例  
 在本方案中，当 User1 尝试提交更改时将引发 <xref:System.Data.Linq.ChangeConflictException> 异常，原因是 User2 同时已更改了 Assistant 和 Department 列。 下表说明了这种情况。  
  
||经理|Assistant|Department|  
|------|-------------|---------------|----------------|  
|原始数据库在被 User1 和 User2 查询时的状态。|Alfreds|Maria|销售额|  
|User1 准备提交这些更改。|Alfred||“营销”|  
|User2 已经提交了这些更改。||Mary|服务|  
  
 User1 决定通过将数据库值与当前客户端成员值合并来解决此冲突。 结果将是，数据库值仅在当前变更集也修改了该值时才会被覆盖。  
  
 User1 通过使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 解决了此冲突后，数据库中的结果将如下表所示：  
  
||经理|Assistant|Department|  
|------|-------------|---------------|----------------|  
|解决冲突后的新状态。|Alfred<br /><br /> （来自 User1）|Mary<br /><br /> （来自 User2）|“营销”<br /><br /> （来自 User1）|  
  
 下面的示例演示如何将数据库值与当前客户端成员值合并（除非此客户端也已经更改了该值）。 未对各个成员冲突进行检查或自定义处理。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [如何：通过重写数据库值解决冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [如何：通过保留数据库值解决冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [如何：管理更改冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
