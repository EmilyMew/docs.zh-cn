---
title: 如何：将更改提交到数据库
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 572c4427ada06701c5982770ae476bd1c6c2b13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082537"
---
# <a name="how-to-submit-changes-to-the-database"></a>如何：将更改提交到数据库
无论您对对象做了多少项更改，都只是在更改内存中的副本。 您并未对数据库中的实际数据做任何更改。 直到您对 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 显式调用 <xref:System.Data.Linq.DataContext>，您所做的更改才会传输到服务器。  
  
 当您进行此调用时，<xref:System.Data.Linq.DataContext> 会设法将您所做的更改转换为等效的 SQL 命令。 可以使用你自己的自定义逻辑来重写这些操作，但由服务的协调的提交顺序<xref:System.Data.Linq.DataContext>称为*更改处理器*。 事件的顺序如下：  
  
1.  当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会检查已知对象的集合以确定新实例是否已附加到它们。 如果已附加，这些新实例将添加到被跟踪对象的集合。  
  
2.  所有具有挂起更改的对象将按照它们之间的依赖关系排序成一个对象序列。 如果一个对象的更改依赖于其他对象，则这个对象将排在其依赖项之后。  
  
3.  在即将传输任何实际更改时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会启动一个事务来包装由各条命令组成的系列。  
  
4.  对对象的更改会逐个转换为 SQL 命令，然后发送到服务器。  
  
 此时，如果数据库检测到任何错误，都会造成提交进程停止并引发异常。 将回滚对数据库的所有更改，就像未进行过提交一样。 <xref:System.Data.Linq.DataContext> 仍具有所有更改的完整记录。 因此你可以设法修正问题并重新调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>，就像下面的代码示例中那样。  
  
## <a name="example"></a>示例  
 用于执行提交的事务成功完成后，<xref:System.Data.Linq.DataContext> 就会通过忽略更改跟踪信息接受对对象的更改。  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [如何：检测到并解决冲突的提交](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [如何：管理更改冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [下载示例数据库](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [进行和提交数据更改](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
