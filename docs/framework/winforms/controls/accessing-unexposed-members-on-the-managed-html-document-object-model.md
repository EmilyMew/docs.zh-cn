---
title: 在托管 HTML 文档对象模型中访问未公开成员
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129501"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>在托管 HTML 文档对象模型中访问未公开成员
托管 HTML 文档对象模型 (DOM) 包含一个名为类<xref:System.Windows.Forms.HtmlElement>公开属性、 方法和事件的所有 HTML 元素都有共同点。 有时，但是，你将需要访问托管的接口不会直接公开的成员。 本主题介绍两种方法可访问未公开的成员，包括[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]和网页中定义的 VBScript 函数。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>通过托管接口访问未公开的成员  
 <xref:System.Windows.Forms.HtmlDocument> 和<xref:System.Windows.Forms.HtmlElement>提供四种方法来访问未公开成员。 下表显示类型和其相应的方法。  
  
|成员类型|方法|  
|-----------------|-----------------|  
|属性 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|方法|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 当使用这些方法时，假定您具有正确的基础类型的元素。 假设你想要收听`Submit`的事件`FORM`上对应的 HTML 元素页上，因此，你可以在执行一些预处理`FORM`的值之前用户将其提交到服务器。 理想情况下，如果你可以控制 HTML，您需要定义`FORM`具有一个唯一`ID`属性。  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 加载到此页后<xref:System.Windows.Forms.WebBrowser>控件，可以使用<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>方法来检索`FORM`在运行的时使用`form1`作为自变量。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>访问非托管的接口  
 此外可以通过使用由每个 DOM 类公开的非托管的组件对象模型 (COM) 接口访问托管 HTML DOM 上的未公开的成员。 如果需要进行多次调用未公开成员，或未公开的成员返回不使用托管 HTML DOM 的包装其他非托管的接口是建议这样做  
  
 下表显示了所有托管 HTML dom。 通过公开的非托管接口 单击每个链接的说明其用途和有关示例代码。  
  
|类型|非托管的接口|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 使用 COM 接口的最简单方法是添加到非托管 HTML DOM 库 (MSHTML.dll) 的引用从应用程序，虽然这是不受支持。 有关详细信息，请参阅[知识库文章 934368](https://support.microsoft.com/kb/934368)。  
  
## <a name="accessing-script-functions"></a>访问脚本函数  
 HTML 页可以定义一个或多个函数，通过使用一种脚本语言，如[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]或 VBScript。 这些函数的内部放置`SCRIPT`页在页中，并可对 DOM 按需或响应的事件中运行  
  
 可以调用任何脚本函数定义在 HTML 页使用<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法。 如果脚本方法返回一个 HTML 元素，您可以使用强制转换将转换到此返回结果<xref:System.Windows.Forms.HtmlElement>。 有关详细信息和代码示例，请参阅<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。  
  
## <a name="see-also"></a>请参阅

- [使用托管 HTML 文档对象模型](using-the-managed-html-document-object-model.md)
