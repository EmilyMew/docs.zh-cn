---
title: Visual Basic 应用程序模型概述
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 02cc71dbda47d078284d9a2ec07538dfa063ac75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819757"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic 应用程序模型概述
Visual Basic 提供定义完善的模型，用于控制 Windows 窗体应用程序的行为： Visual Basic 应用程序模型。 此模型包括用于处理应用程序的启动和关闭，以及用于捕获未经处理的异常事件的事件。 它还提供用于开发单实例应用程序的支持。 应用程序模型是可扩展的因此需要更多控制的开发人员可以自定义其可重写方法。  
  
## <a name="uses-for-the-application-model"></a>应用程序模型的用途  
 典型的应用程序需要它启动和关闭时执行任务。 例如，它启动时，应用程序可以显示初始屏幕、 建立数据库连接、 加载已保存的状态等。 当应用程序关闭时，它可以关闭数据库连接、 保存当前状态，等等。 此外，应用程序可以执行特定的代码，该应用程序关闭后在的情况下，此类未经处理的异常。  
  
 Visual Basic 应用程序模型可以轻松创建*单实例*应用程序。 单实例应用程序不同一次可以正常的应用程序中的运行的应用程序只有一个实例。 尝试启动单实例应用程序的另一个实例会导致在收到通知的原始实例 — 通过`StartupNextInstance`事件，另一次启动尝试所做的。 该通知包括后续实例的命令行参数。 然后才能进行任何初始化，然后关闭应用程序的后续实例。  
  
 单实例应用程序启动，并检查它是否为第一个实例或应用程序的后续实例：  
  
-   如果它是第一个实例，它将正常启动。  
  
-   每个后续尝试启动应用程序，第一个实例时，会导致非常不同的行为。 后续尝试通知有关命令行参数，第一个实例，随后立即退出。 第一个实例句柄`StartupNextInstance`事件来确定后续实例的命令行参数，并继续运行。  
  
     此图显示了后续实例发出的第一个实例的信号：  
  
     ![图示显示单实例应用程序映像。](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 通过处理`StartupNextInstance`事件，您可以控制单实例应用程序的行为方式。 例如，Microsoft Outlook 通常运行作为单实例应用程序;当 Outlook 正在运行，在尝试启动 Outlook 时同样，重心转移到原始实例，但不会打开另一个实例。  
  
## <a name="events-in-the-application-model"></a>应用程序模型中的事件  
 在应用程序模型中找到以下事件：  
  
-   **应用程序启动**。 应用程序将引发<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>事件启动时。 通过处理此事件，你可以添加在加载主窗体之前初始化应用程序的代码。 `Startup`事件还提供了用于取消执行启动过程中，在该阶段的应用程序的必要。  
  
     可以配置要显示的初始屏幕，当应用程序启动代码在运行时的应用程序。 默认情况下，应用程序模型将取消显示初始屏幕上时既`/nosplash`或`-nosplash`使用命令行参数。  
  
-   **单实例应用程序**。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>单实例应用程序的后续实例启动时引发事件。 该事件传递的后续实例的命令行参数。  
  
-   **未经处理的异常**。 如果应用程序遇到未经处理的异常，它会发出<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>事件。 该事件的处理程序可以检查异常，并确定是否要继续执行。  
  
     `UnhandledException`不在某些情况下会引发事件。 有关详细信息，请参阅 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。  
  
-   **网络连接更改**。 如果计算机的网络可用性更改，应用程序将引发<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>事件。  
  
     `NetworkAvailabilityChanged`不在某些情况下会引发事件。 有关详细信息，请参阅 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
-   **应用程序关闭**。 该应用程序提供<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>即将关闭时发出信号通知的事件。 这种情况下处理程序中，你可以确保，操作你的应用程序需要对其执行 — 关闭并保存，例如 — 都已完成。 你可以配置你的应用程序主窗体关闭时，关闭或要关闭的情况下仅当所有窗体关闭。  
  
## <a name="availability"></a>可用性  
 默认情况下，Visual Basic 应用程序模型是适用于 Windows 窗体项目。 如果应用程序配置为使用不同的启动对象，或使用自定义启动应用程序代码`Sub Main`，则该对象或类可能需要提供的实现<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>类，以使用应用程序模型。 有关更改启动对象的信息，请参阅[应用程序页，项目设计器 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [扩展 Visual Basic 应用程序模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
