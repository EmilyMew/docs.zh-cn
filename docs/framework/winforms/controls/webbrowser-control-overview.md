---
title: WebBrowser 控件概述
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: c75d0b348a2f3dd678f2bfb235bce2e4e227c4b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109430"
---
# <a name="webbrowser-control-overview"></a>WebBrowser 控件概述
<xref:System.Windows.Forms.WebBrowser>控件提供 WebBrowser ActiveX 控件托管的包装。 托管的包装，可以在 Windows 窗体客户端应用程序中显示网页。 可以使用<xref:System.Windows.Forms.WebBrowser>控件重复中你的应用程序或你的 Internet Explorer Web 浏览功能可以禁用默认 Internet 资源管理器功能并将该控件用作简单的 HTML 文档查看器。 此外可以使用该控件将基于 DHTML 的用户界面元素添加到你的窗体并隐藏这一事实中托管的<xref:System.Windows.Forms.WebBrowser>控件。 此方法可以无缝组合在单个应用程序中的 Windows 窗体控件的 Web 控件。  
  
## <a name="frequently-used-properties-methods-and-events"></a>常用的属性、 方法和事件  
 <xref:System.Windows.Forms.WebBrowser>控件具有多个属性、 方法和事件，可以用于实现 Internet Explorer 中的控件。 例如，可以使用`Navigate`方法以实现地址栏中，并`GoBack`， `GoForward`， `Stop`，和`Refresh`方法来实现导航按钮在工具栏上。 您可以处理`Navigated`事件使用的值更新地址栏`Url`属性和值为标题栏`DocumentTitle`属性。  
  
 如果你想要生成您自己应用程序中的页内容，则可以设置`DocumentText`属性。 如果您熟悉 HTML 文档对象模型 (DOM)，您还可以操作通过在当前网页的内容`Document`属性。 通过此属性，可以存储和修改文档在内存中而不是文件之间导航。  
  
 `Document`属性，您还可以调用在网页脚本在客户端应用程序代码中的代码中实现的方法。 若要从脚本代码访问客户端应用程序代码中，设置`ObjectForScripting`属性。 作为脚本代码时可以访问你指定的对象`window.external`对象。  
  
|名称|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 属性|获取一个对象，提供对当前网页的 HTML 文档对象模型 (DOM) 的托管的访问。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Event — 事件|Web 页面完成加载时发生。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 属性|获取或设置当前网页的内容的 HTML。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 属性|获取当前网页的标题。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|导航到历史记录中的上一页。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|导航到历史记录中的下一页。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|导航到指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> Event — 事件|导航开始时，启用要取消的操作之前发生。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 属性|获取或设置脚本代码的网页可以使用与你的应用程序进行通信的对象。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|打印当前网页。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重新加载当前网页。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|停止当前导航并停止动态页元素，如声音与动画。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 属性|获取或设置当前网页的 URL。 设置此属性导航到新 URL 的控件。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [如何：使用 WebBrowser 控件导航到 URL](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [如何：使用 WebBrowser 控件打印](how-to-print-with-a-webbrowser-control.md)
- [如何：向 Windows 窗体应用程序添加 Web 浏览器功能](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [如何：在 Windows 窗体应用程序中创建 HTML 文档查看器](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [如何：在 DHTML 代码和客户端应用程序代码之间实现双向通信](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser 安全](webbrowser-security.md)
