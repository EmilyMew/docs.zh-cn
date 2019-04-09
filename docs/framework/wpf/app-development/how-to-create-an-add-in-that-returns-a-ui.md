---
title: 如何：创建返回 UI 的外接程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115741"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>如何：创建返回 UI 的外接程序
此示例演示如何创建 Windows Presentation Foundation (WPF) 返回到主机 WPF 独立应用程序的外接程序。  
  
 外接程序返回一个 UI，WPF 用户控件。 用户控件的内容是单个按钮，单击时会显示消息框。 WPF 独立应用程序承载外接程序，并显示主应用程序窗口的内容 （由外接程序返回） 的用户控件。  
  
 **系统必备**  
  
 此示例重点介绍启用此方案中，WPF 扩展到.NET Framework 外接程序模型，并假设条件如下：  
  
-   了解.NET Framework 外接程序模型，包括管道、 外接程序和主机开发。 如果您不熟悉这些概念，请参阅[外接程序和扩展性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 有关演示如何实现一个管道、 外接程序和主机应用程序的教程，请参阅[演练：创建可扩展的应用程序](../../add-ins/walkthrough-create-extensible-app.md)。  
  
-   .NET Framework 外接程序模型，可以在此处找到的 WPF 扩展知识：[WPF 外接程序概述](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>示例  
 若要返回 WPF UI 的外接程序创建的每个管道段、 外接程序和主机应用程序需要特定代码。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>实现协定管道段  
 必须通过返回 UI 的协定定义的方法和它的返回值的类型必须是<xref:System.AddIn.Contract.INativeHandleContract>。 这可通过演示`GetAddInUI`方法的`IWPFAddInContract`协定在下面的代码。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>实现外接程序视图管道段  
 由于外接程序实现[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]它提供了作为类的子类<xref:System.Windows.FrameworkElement>，与相关联的外接程序视图上的方法`IWPFAddInView.GetAddInUI`必须返回类型的值<xref:System.Windows.FrameworkElement>。 以下代码显示作为接口实现的协定的外接程序视图。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>实现外接程序端适配器管道段  
 协定方法返回<xref:System.AddIn.Contract.INativeHandleContract>，但外接程序返回<xref:System.Windows.FrameworkElement>（如指定的外接程序视图）。 因此，<xref:System.Windows.FrameworkElement>必须转换为<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔离边界。 这一工作由外接程序端适配器通过调用执行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下面的代码中所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>实现主机视图管道段  
 由于主机应用程序将显示<xref:System.Windows.FrameworkElement>，与相关联的主机视图上的方法`IWPFAddInHostView.GetAddInUI`必须返回类型的值<xref:System.Windows.FrameworkElement>。 以下代码显示作为接口实现的协定的主机视图。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>实现主机端适配器管道段  
 协定方法返回<xref:System.AddIn.Contract.INativeHandleContract>，但主机应用程序预期<xref:System.Windows.FrameworkElement>（如主机视图所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必须转换为<xref:System.Windows.FrameworkElement>后跨越隔离边界。 由主机端适配器通过调用执行这项工作<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，如下面的代码中所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>实现外接程序  
 外接程序端适配器和外接程序视图创建之后外, 接程序 (`WPFAddIn1.AddIn`) 必须实现`IWPFAddInView.GetAddInUI`方法返回<xref:System.Windows.FrameworkElement>对象 (<xref:System.Windows.Controls.UserControl>在此示例中)。 实现<xref:System.Windows.Controls.UserControl>， `AddInUI`，下面的代码所示。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 实现`IWPFAddInView.GetAddInUI`由外接程序仅需返回的新实例`AddInUI`，如下面的代码所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>实现主机应用程序  
 主机端适配器和主机视图创建，主机应用程序可以使用.NET Framework 外接程序模型打开管道、 获取的宿主视图的外接程序，并调用`IWPFAddInHostView.GetAddInUI`方法。 这些步骤在以下代码中显示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>请参阅

- [外接程序和扩展性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 外接程序概述](wpf-add-ins-overview.md)
