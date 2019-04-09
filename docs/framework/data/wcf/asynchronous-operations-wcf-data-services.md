---
title: 异步操作（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: ef41b458a3f5b977eaaff523413c1a8d3b1982a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126630"
---
# <a name="asynchronous-operations-wcf-data-services"></a>异步操作（WCF 数据服务）
与内部网络中运行的应用程序相比，Web 应用程序必须适应客户端与服务器之间更长时间的延迟。 若要优化应用程序的性能和用户体验，建议你在通过 Web 访问 <xref:System.Data.Services.Client.DataServiceContext> 服务器时使用 <xref:System.Data.Services.Client.DataServiceQuery%601> 和 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 类的异步方法。  
  
 尽管 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 服务器异步处理 HTTP 请求，但是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 客户端库的某些方法是同步的，并且会一直等到整个请求-响应交换完成后才会继续执行。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 客户端库的异步方法不会等待此交换完成，并且允许应用程序同时保持具有响应能力的用户界面。  
  
 可以通过使用上一对方法执行异步操作<xref:System.Data.Services.Client.DataServiceContext>并<xref:System.Data.Services.Client.DataServiceQuery%601>开头的类*开始*并*最终*分别。 *开始*方法注册服务时，才完成操作调用的委托。 *最终*应注册为处理来自已完成的操作的回调的委托中调用方法。 当您调用*最终*方法以完成异步操作，则必须从同一个进行<xref:System.Data.Services.Client.DataServiceQuery%601>或<xref:System.Data.Services.Client.DataServiceContext>用于开始该操作的实例。 每个*开始*方法采用`state`可以将状态对象传递给回调的参数。 此状态对象从<xref:System.IAsyncResult>后者随回调提供，用于调用对应*最终*方法以完成异步操作。 例如，如果在对 <xref:System.Data.Services.Client.DataServiceQuery%601> 实例调用 `state` 方法时提供该实例作为 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 参数，那么 <xref:System.Data.Services.Client.DataServiceQuery%601> 将返回同一个 <xref:System.IAsyncResult> 实例。 随后将使用 <xref:System.Data.Services.Client.DataServiceQuery%601> 的这个实例调用 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法以完成查询操作。 有关详细信息，请参阅[如何：执行异步数据服务查询](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)。  
  
> [!NOTE]
>  .NET Framework for Silverlight 中提供的客户端库仅支持异步操作。 有关详细信息，请参阅[WCF 数据服务 (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)。  
  
 .NET Framework 客户端库支持下列异步操作：  
  
|操作|方法|  
|---------------|-------------|  
|执行 <xref:System.Data.Services.Client.DataServiceQuery%601>。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|从 <xref:System.Data.Services.Client.DataServiceContext> 执行查询。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|从 <xref:System.Data.Services.Client.DataServiceContext> 执行批查询。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|将相关实体加载到 <xref:System.Data.Services.Client.DataServiceContext> 中。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|将更改保存到中的对象 <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>异步操作的线程注意事项  
 多线程应用程序中注册为异步操作的回调调用委托时不一定是用于调用同一线程上*开始*方法，即创建初始请求。 其中必须在特定线程中调用回调的应用程序，您必须显式执行封送的*最终*方法，用于处理对所需线程的响应。 例如，在基于 Windows Presentation Foundation (WPF) 的应用程序和基于 Silverlight 的应用程序中，必须通过对 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 对象使用 <xref:System.Windows.Threading.Dispatcher> 方法，将响应封送回 UI 线程。 有关详细信息，请参阅[查询数据服务 (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95))。  
  
## <a name="see-also"></a>请参阅

- [WCF 数据服务客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
