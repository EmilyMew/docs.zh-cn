---
title: 数据并行（任务并行库）
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3450908cadff453df79ab8fcf10285c25dfa50a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976221"
---
# <a name="data-parallelism-task-parallel-library"></a>数据并行（任务并行库）
*数据并行*指的是对源集合或数组的元素同时（即，并行）执行相同操作的场景。 在数据并行操作中，对源集合进行分区，以便多个线程能够同时在不同的网段上操作。  
  
 任务并行库 (TPL) 支持通过 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 类实现的数据并行。 此类对 [for](~/docs/csharp/language-reference/keywords/for.md) 循环和 [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) 循环（Visual Basic 中的 `For` 和 `For Each`）提供了基于方法的并行执行。 你为 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 循环编写的循环逻辑与编写连续循环的相似。 无需创建线程或列工作项。 在基本循环中，不需要加锁。 TPL 为你处理所有低级别的工作。 有关使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 的详细信息，请下载文档[并行编程模式：了解并应用与 .NET Framework 4 的并行模式](https://www.microsoft.com/download/details.aspx?id=19222)。 下面的代码示例演示了一个简单的 `foreach` 循环及其并行等效项。  
  
> [!NOTE]
>  本文档使用 lambda 表达式在 TPL 中定义委托。 如果不熟悉 C# 或 Visual Basic 中的 lambda 表达式，请参阅 [PLINQ 和 TPL 中的 Lambda 表达式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 并行循环运行时，TPL 将数据源进行分区，以便该循环可以同时对多个部分进行作用。 在后台，任务计划程序基于系统资源和工作负荷来划分任务。 如有可能，如果工作负荷变得不平衡了，计划程序将重新分配多个线程与处理器之间的工作。  
  
> [!NOTE]
>  你也可以提供你自己的自定义分区程序或计划程序。 有关详细信息，请参阅 [PLINQ 和 TPL 的自定义分区程序](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)和[任务计划程序](xref:System.Threading.Tasks.TaskScheduler)。  
  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法都有多个过载，可让你停止或中断循环执行，监视其它线程上循环的状态，保持本地线程状态，完成本地线程对象，控制并发程度等等。 启用此功能的帮助器类型包括 <xref:System.Threading.Tasks.ParallelLoopState>、<xref:System.Threading.Tasks.ParallelOptions>、<xref:System.Threading.Tasks.ParallelLoopResult>、<xref:System.Threading.CancellationToken> 和 <xref:System.Threading.CancellationTokenSource>。  
  
 有关详细信息，请参阅[并行编程模式：了解并应用与 .NET Framework 4 的并行模式](https://www.microsoft.com/download/details.aspx?id=19222)。  
  
 PLINQ 支持使用声明性或查询类语法的数据并行。 有关详细信息，请参阅[并行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|Title|说明|  
|-----------|-----------------|  
|[如何：编写简单的 Parallel.For 循环](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|描述如何编写遍历任何数组或可变址 <xref:System.Collections.Generic.IEnumerable%601> 源集合的 <xref:System.Threading.Tasks.Parallel.For%2A> 循环。|  
|[如何：编写简单的 Parallel.ForEach 循环](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|描述如何编写遍历任何 <xref:System.Collections.Generic.IEnumerable%601> 源集合的 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 循环。|  
|[如何：从 Parallel.For 循环停止或中断](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|描述如何停止或中断并行循环，以便所有线程都获得该操作的通知。|  
|[如何：编写具有线程局部变量的 Parallel.For 循环](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|描述如何编写 <xref:System.Threading.Tasks.Parallel.For%2A> 循环，该循环中每个线程都维持有对其它任何线程不可见的私有变量，以及如何在循环完成时，同步所有线程的结果。|  
|[如何：使用分区本地变量编写 Parallel.ForEach 循环](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|描述如何编写 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 循环，该循环中每个线程都维持有对其它任何线程不可见的私有变量，以及如何在循环完成时，同步所有线程的结果。|  
|[如何：取消 Parallel.For 或 ForEach 循环](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|描述如何通过使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 取消并行循环|  
|[如何：加快小型循环主体的速度](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|描述在循环主体极小时加快执行速度的方法。|  
|[任务并行库 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|提供任务并行库的概述。|  
|[并行编程](../../../docs/standard/parallel-programming/index.md)|介绍.NET Framework 中的并行编程。|  
  
## <a name="see-also"></a>请参阅

- [并行编程](../../../docs/standard/parallel-programming/index.md)
