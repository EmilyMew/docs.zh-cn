---
title: 如何：创建作为 UI 的外接程序
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 9b7fa33d9af8d364491d1c72813cb62f34378557
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100296"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>如何：创建作为 UI 的外接程序
此示例演示如何为 Windows Presentation Foundation (WPF) 的 WPF 独立应用程序是托管的外接程序创建。  
  
 外接程序是一个 UI，WPF 用户控件。 用户控件的内容是单个按钮，单击时会显示消息框。 WPF 独立应用程序托管加载项 UI 为应用程序主窗口的内容。  
  
 **系统必备**  
  
 此示例重点介绍启用此方案中，WPF 扩展到.NET Framework 外接程序模型，并假设条件如下：  
  
-   了解.NET Framework 外接程序模型，包括管道、 外接程序和主机开发。 如果您不熟悉这些概念，请参阅[外接程序和扩展性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 有关演示如何实现一个管道、 外接程序和主机应用程序的教程，请参阅[演练：创建可扩展的应用程序](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。  
  
-   .NET Framework 外接程序模型的 WPF 扩展的知识。 请参阅[WPF 外接程序概述](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>示例  
 是一个 WPF UI 的外接程序创建的每个管道段、 外接程序和主机应用程序需要特定代码。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>实现协定管道段  
 当外接程序是一个 UI 时，必须实现外接程序的协定<xref:System.AddIn.Contract.INativeHandleContract>。 在示例中，`IWPFAddInContract`实现<xref:System.AddIn.Contract.INativeHandleContract>，如下面的代码中所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>实现外接程序视图管道段  
 由于外接程序作为实现的子类<xref:System.Windows.FrameworkElement>类型外, 接程序视图还必须子类<xref:System.Windows.FrameworkElement>。 下面的代码显示了为实现的协定的外接程序视图`WPFAddInView`类。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 此处外, 接程序视图派生自<xref:System.Windows.Controls.UserControl>。 因此，加载项 UI 还应派生自<xref:System.Windows.Controls.UserControl>。  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>实现外接程序端适配器管道段  
 协定是<xref:System.AddIn.Contract.INativeHandleContract>外, 接程序是<xref:System.Windows.FrameworkElement>（如指定的外接程序视图管道段）。 因此，<xref:System.Windows.FrameworkElement>必须转换为<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔离边界。 这一工作由外接程序端适配器通过调用执行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下面的代码中所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 在其中的外接程序返回 UI 的外接程序模型 (请参阅[创建外接程序，将返回的用户界面](how-to-create-an-add-in-that-returns-a-ui.md)) 外, 接程序适配器转换<xref:System.Windows.FrameworkElement>到<xref:System.AddIn.Contract.INativeHandleContract>通过调用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 必须也调用该模型中，尽管您需要实现一种方法从其编写代码来调用它。 执行此操作通过重写<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>和实现调用的代码<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>如果正在调用的代码<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>应为<xref:System.AddIn.Contract.INativeHandleContract>。 在此情况下，调用方将为主机端适配器，这在后续子节中有所介绍。  
  
> [!NOTE]
>  此外需要重写<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>在此模型中使用 tab 键切换之间主机应用程序 UI 和外接程序用户界面。 详细信息，请参阅"WPF 外接程序限制"中[WPF 外接程序概述](wpf-add-ins-overview.md)。  
  
 由于外接程序端适配器实现派生自的接口<xref:System.AddIn.Contract.INativeHandleContract>，还需要实现<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，但忽略此时<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>被重写。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>实现主机视图管道段  
 在此模型中，主机应用程序通常预期主机视图为<xref:System.Windows.FrameworkElement>子类。 主机端适配器必须将转换<xref:System.AddIn.Contract.INativeHandleContract>到<xref:System.Windows.FrameworkElement>后<xref:System.AddIn.Contract.INativeHandleContract>跨越隔离边界。 因为没有要获取的主机应用程序通过调用方法<xref:System.Windows.FrameworkElement>，主机视图必须"return"<xref:System.Windows.FrameworkElement>由包含它。 因此，主机视图必须派生自的子类<xref:System.Windows.FrameworkElement>，可以包含其他[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，如<xref:System.Windows.Controls.UserControl>。 下面的代码显示作为实现的协定的主机视图`WPFAddInHostView`类。  

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>实现主机端适配器管道段  
 协定是<xref:System.AddIn.Contract.INativeHandleContract>，主机应用程序预期<xref:System.Windows.Controls.UserControl>（如主机视图所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必须转换为<xref:System.Windows.FrameworkElement>之后才能设置为主机视图的内容跨越隔离边界，(派生自<xref:System.Windows.Controls.UserControl>)。  
  
 这一工作由主机端适配器执行，如以下代码所示。  

 如您所见，宿主端适配器将获取<xref:System.AddIn.Contract.INativeHandleContract>通过调用外接程序端适配器<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>方法 (这一点其中<xref:System.AddIn.Contract.INativeHandleContract>跨越隔离边界)。  
  
 主机端适配器，然后将转换<xref:System.AddIn.Contract.INativeHandleContract>到<xref:System.Windows.FrameworkElement>通过调用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。 最后，<xref:System.Windows.FrameworkElement>设置为主机视图的内容。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>实现外接程序  
 外接程序端适配器和外接程序视图就位后，外接程序就可以通过派生自外接程序视图来实现，如以下代码所示。  

 从示例中，可以看到此模型的一个突出优点： 外接程序开发人员只需实现外接程序 （因为它是 UI 也），而不是同时外接程序类和外接程序的 UI。  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>实现主机应用程序  
 主机端适配器和主机视图创建，主机应用程序可以使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]外接程序模型打开管道并获取外接程序的宿主视图。 这些步骤在以下代码中显示。  

 主机应用程序使用典型的.NET Framework 外接程序模型代码激活外接程序，它将隐式返回到主机应用程序宿主视图。 主机应用程序随后显示主机视图 (即<xref:System.Windows.Controls.UserControl>) 从<xref:System.Windows.Controls.Grid>。  
  
 用于处理与外接程序 UI 代码在外接程序的应用程序域中运行。 这些交互包括以下内容：  
  
-   处理<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
-   显示<xref:System.Windows.MessageBox>。  
  
 此活动完全独立于主机应用程序。  
  
## <a name="see-also"></a>请参阅

- [外接程序和扩展性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 外接程序概述](wpf-add-ins-overview.md)
