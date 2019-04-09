---
title: 如何：确定此时是否可以打印一项打印作业
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: dab836af8ba3d177719d910142cd93f8f6de0002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099851"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>如何：确定此时是否可以打印一项打印作业
打印队列并不总是可用的一天 24 小时。 它们具有开始和结束时间属性可以设置以使其在一天中的某些时间不可用。 例如，此功能可用于保留专供特定部门的下午 5 点后的打印机。 该部门必须使用其他队列服务比其他部门的打印机。 将设置为其他部门队列以在下午 5 点后将不可用，而队列支持的部门可能被设置为始终可用。  
  
 此外，可以设置打印作业本身是可打印仅在指定的时间范围内。  
  
 <xref:System.Printing.PrintQueue>并<xref:System.Printing.PrintSystemJobInfo>类中公开[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]的 Microsoft.NET Framework 提供一种远程检查是否给定的打印作业可以打印到给定队列的当前时间。  
  
## <a name="example"></a>示例  
 下面的示例是一个示例，可以诊断问题的打印作业。  
  
 有两个主要步骤为此类型的函数，如下所示。  
  
1.  读取<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>并<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>的属性<xref:System.Printing.PrintQueue>以确定它们之间是否为当前时间。  
  
2.  读取<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>并<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>的属性<xref:System.Printing.PrintSystemJobInfo>以确定它们之间是否为当前时间。  
  
 但问题变复杂了这些属性不在于<xref:System.DateTime>对象。 而是<xref:System.Int32>表示一天的时间为午夜过后的分钟数的对象。 此外，这不是午夜当前所在的时区，但午夜 UTC （协调世界时）。  
  
 第一个代码示例显示的静态方法**ReportQueueAndJobAvailability**，它会传递<xref:System.Printing.PrintSystemJobInfo>和调用帮助程序方法来确定作业是否可以打印在当前时间和，如果它不是，可以打印时。 请注意，<xref:System.Printing.PrintQueue>不传递给方法。 这是因为<xref:System.Printing.PrintSystemJobInfo>包括对中的队列的引用其<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>属性。  
  
 从属方法包含重载**ReportAvailabilityAtThisTime**方法可以采用该方法<xref:System.Printing.PrintQueue>或<xref:System.Printing.PrintSystemJobInfo>作为参数。 此外，还有**TimeConverter.ConvertToLocalHumanReadableTime**。 下面讨论了所有这些方法。  
  
 **ReportQueueAndJobAvailability**方法首先检查以查看队列或打印作业是否不可用这一次。 如果其中任一个不可用，它则会检查以查看是否不可用队列。 如果不可用，则该方法报告这一事实以及当队列将再次变得可用的时间。 然后会检查该作业，如果不可用，它报告的下一个时间跨度时它时它可以打印。 最后，该方法将报告该作业可以打印时的最早时间。 这是更高版本的以下两次。  
  
-   打印队列接下来可用的时间。  
  
-   打印作业下一步可用的时间。  
  
 报告一天中的时间时<xref:System.DateTime.ToShortTimeString%2A>也称为方法，因为此方法取消年、 月和天的输出。 打印队列或打印作业的可用性限于在特定的年、 月或天。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 两个重载**ReportAvailabilityAtThisTime**方法是相同类型传递给它们，因此，只有除外<xref:System.Printing.PrintQueue>版本如下所示。  
  
> [!NOTE]
>  这一事实的方法是相同类型除外引发的问题，该示例不会创建一个泛型方法的原因**ReportAvailabilityAtThisTime\<T >**。 原因是此类方法需要被限制为具有的类**StartTimeOfDay**并**UntilTimeOfDay**属性，该方法调用，但泛型方法均仅受限于单一类和唯一的类共有<xref:System.Printing.PrintQueue>并<xref:System.Printing.PrintSystemJobInfo>在继承树是<xref:System.Printing.PrintSystemObject>其中没有任何此类属性。  
  
 **ReportAvailabilityAtThisTime**方法 （如下面的代码示例所示） 首先初始化<xref:System.Boolean>sentinel 变量`true`。 将重置为`false`，如果队列不可用。  
  
 接下来，该方法将检查以查看是否开始和 until 时间是否相同。 如果是，队列是始终可用，因此该方法将返回`true`。  
  
 如果队列不可用的时间，该方法将使用静态<xref:System.DateTime.UtcNow%2A>属性来获取当前时间作为<xref:System.DateTime>对象。 (我们不需要本地时间，因为<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>属性本身就是以 UTC 时间。)  
  
 但是，这两个属性不是<xref:System.DateTime>对象。 它们是<xref:System.Int32>将时间表示为分钟后 UTC 午夜的数字。 因此我们需要转换我们<xref:System.DateTime>午夜分钟后的对象。 完成后，该方法只需检查以查看是否"立即"是队列的开始之间和"截至"时间设置为 false，如果"现在"sentinel 之间两次，并不返回 sentinel。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime**方法 （如下面的代码示例所示） 不使用任何方法引入了使用 Microsoft.NET Framework，因此进行简要的讨论。 该方法具有一个双精度的转换任务： 它必须采用一个整型表示午夜之后的分钟，并将其转换为人工可读的时间和它必须将其转换为本地时间。 这是通过实现通过首先创建<xref:System.DateTime>对象，它设置为午夜 UTC，然后使用<xref:System.DateTime.AddMinutes%2A>方法添加到该方法传递的分钟数。 这将返回一个新<xref:System.DateTime>传递给该方法将原始时间表示。 <xref:System.DateTime.ToLocalTime%2A>方法然后将此转换为本地时间。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF 中的文档](documents-in-wpf.md)
- [打印概述](printing-overview.md)
