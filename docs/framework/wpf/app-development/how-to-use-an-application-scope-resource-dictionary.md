---
title: 如何：使用应用程序范围资源字典
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 589e28b3c05496e3fc17055b98240e389faed068
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125369"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>如何：使用应用程序范围资源字典
本示例显示如何定义和使用应用程序范围的自定义资源字典。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Application> 公开共享资源的应用程序作用域存储： <xref:System.Windows.Application.Resources%2A>。 默认情况下<xref:System.Windows.Application.Resources%2A>属性使用的实例初始化<xref:System.Windows.ResourceDictionary>类型。 可以使用此实例时获取和设置应用程序作用域属性使用<xref:System.Windows.Application.Resources%2A>。 有关详细信息，请参阅[如何：获取和设置应用程序范围资源](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100))。
  
 如果必须使用设置的多个资源<xref:System.Windows.Application.Resources%2A>，而是可以使用自定义资源字典来存储这些资源和设置<xref:System.Windows.Application.Resources%2A>与之相反。 下面演示如何声明使用 XAML 的自定义资源字典。
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 交换使用整个资源字典<xref:System.Windows.Application.Resources%2A>使您能够支持应用程序范围的主题，其中每个主题封装由单个资源字典。 下面的示例演示如何设置 <xref:System.Windows.ResourceDictionary>。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 下面演示了如何从通过公开的资源字典获取应用程序范围资源<xref:System.Windows.Application.Resources%2A>在 XAML 中。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 以下内容显示如何也能获取代码中的资源。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 有两个注意事项，以便使用<xref:System.Windows.Application.Resources%2A>。 首先，字典*密钥*是一个对象，因此必须使用完全相同的对象实例时设置和获取属性值。 （请注意，使用字符串时键区分大小写。）其次，字典*值*是一个对象，因此必须将值转换为所需的类型，获取属性值时。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [XAML 资源](../advanced/xaml-resources.md)
- [合并资源字典](../advanced/merged-resource-dictionaries.md)
