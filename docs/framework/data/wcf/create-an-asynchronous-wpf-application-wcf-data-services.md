---
title: 如何：创建异步 Windows Presentation Framework 应用程序 （WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 50dc004a94669411c9030f142fc63d154bcde63f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095537"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>如何：创建异步 Windows Presentation Framework 应用程序 （WCF 数据服务）
通过 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，可以将从数据服务获取的数据绑定到 Windows Presentation Framework (WPF) 应用程序的用户界面元素。 有关详细信息，请参阅[数据绑定到控件](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。以异步方式，从而使应用程序可继续响应等待对数据服务请求的响应时，还可以执行对数据服务执行的操作。 若要对数据服务进行异步访问，必须使用适用于 Silverlight 的应用程序。 有关详细信息，请参阅[异步操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
 本主题介绍如何对数据服务进行异步访问并将结果绑定到 WPF 应用程序的元素。 本主题中的示例使用 Northwind 示例数据服务和自动生成的客户端数据服务类。 完成后，将创建此服务和客户端数据类[WCF Data Services 快速入门](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>示例  
 以下是定义 WPF 应用程序窗口的 XAML。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>示例  
 该 XAML 文件的以下代码隐藏页通过使用数据服务执行一个异步查询，并将结果绑定到 WPF 窗口中的元素。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>请参阅

- [WCF 数据服务客户端库](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
