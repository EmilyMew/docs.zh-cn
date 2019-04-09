---
title: .NET 中的并行编程
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b5426f5af9cd6ca919d8da0de0acfed76a2e63
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970384"
---
# <a name="parallel-programming-in-net"></a>.NET 中的并行编程

许多个人计算机和工作站都有多个 CPU 内核，以便多个线程能够同时执行。 为了利用硬件，你可以对代码进行并行化，以将工作分摊在多个处理器上。

过去，并行化需要线程和锁的低级操作。 Visual Studio 和 .NET Framework 提供了运行时、类库类型和诊断工具，从而增强了对并行编程的支持。 .NET Framework 4 中引入的这些功能简化了并行开发。 你可以通过固有方法编写高效、细化且可伸缩的并行代码，而不必直接处理线程或线程池。

下图简要概述了 .NET Framework 中的并行编程体系结构：

![.NET 并行编程体系结构](./media/tpl-architecture.png)

## <a name="related-topics"></a>相关主题

|技术|说明|
|----------------|-----------------|
|[任务并行库 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|提供针对 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 类的文档（包括 `For` 和 `ForEach` 循环的并行版本），还提供了针对 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类的文档（描绘了表示异步操作的首选方式）。|
|[并行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ to Objects 的并行实现，该实现显著提高了许多情况下的性能。|
|[用于并行编程的数据结构](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|提供一些链接，这些链接指向有关线程安全集合类、轻量同步类型以及延迟初始化类型的文档。|
|[并行诊断工具](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|提供一些链接，这些链接指向任务和并行堆栈的 Visual Studio 调试器窗口和[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)的文档。|
|[PLINQ 和 TPL 的自定义分区程序](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|描述分区程序的工作方式，以及如何配置默认分区程序或创建新的分区程序。|
|[任务计划程序](xref:System.Threading.Tasks.TaskScheduler)|描述计划程序的工作方式，以及如何配置默认计划程序。|
|[PLINQ 和 TPL 中的 Lambda 表达式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|简要概述 C# 和 Visual Basic 中的 Lambda 表达式，并演示如何在 PLINQ 和任务并行库中使用这些表达式。|
|[其他阅读材料](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|收录了指向其他信息以及 .NET 中并行编程示例资源的链接。|

## <a name="see-also"></a>请参阅

- [异步概述](../async.md)
- [托管线程](../threading/index.md)
