---
title: 依赖项属性的安全性
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: 85806ee9fb01cd2ca07697230c46a8847fdf8c6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077467"
---
# <a name="dependency-property-security"></a>依赖项属性的安全性
依赖属性通常应当被视为公共属性。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 属性系统在本质上无法对依赖属性值提供安全保证。  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>包装器和依赖属性的访问和安全性  
 通常，依赖属性是随“包装器”[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 属性一起实现的，这些包装器属性可以简化从实例获取或设置属性的过程。 但是，包装器实际上只是方便的方法，实现基础<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>与依赖属性交互时使用的静态调用。 从另外一个角度考虑，这些属性作为恰好由依赖属性（而非私有字段）支持的[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 属性公开。 应用于包装器的安全机制与属性系统行为以及基础依赖属性的访问并不可比。 包装器设置安全要求将只是防止使用便捷方法，但不是会阻止调用<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。 同样，为包装器设置受保护或私有访问级别也不会提供任何有效的安全性。  
  
 如果你正在编写您自己的依赖项属性，应声明包装器和<xref:System.Windows.DependencyProperty>标识符字段为公共成员，以便调用方执行未得到令人误解的该属性的实际访问级别有关的信息 （由于其存储在实现为依赖属性）。  
  
 对于自定义依赖项属性，可以将属性注册为只读依赖属性，并且这确实提供了一种有效方法阻止任何人都不包含对引用设置的属性的<xref:System.Windows.DependencyPropertyKey>该属性。 有关详细信息，请参阅[只读依赖属性](read-only-dependency-properties.md)。  
  
> [!NOTE]
>  声明<xref:System.Windows.DependencyProperty>不禁止标识符字段专用，并想象可用于帮助减少直接公开命名空间的自定义类，但这样的属性不应被视为"私有"作为相同意义上[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]语言定义所定义的访问级别下, 一节中描述的原因。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>依赖属性的属性系统公开  
 它不是通常很有用，并且可能具有误导性，以声明<xref:System.Windows.DependencyProperty>任何访问级别以外的公钥。 该访问级别设置只是防止某人从声明类获得对实例的引用。 但有几个方面的属性系统将返回<xref:System.Windows.DependencyProperty>作为一种标识特定属性，因为它存在于上一个类的实例或派生的类实例，而且该标识符中仍然可以使用<xref:System.Windows.DependencyObject.SetValue%2A>甚至调用如果最初的静态标识符声明为非公共。 此外，<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>虚方法接收的任何现有的依赖属性的值进行了更改的信息。 此外，<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>方法返回具有在本地设置的实例上的任何属性的标识符值。  
  
### <a name="validation-and-security"></a>验证和安全  
 应用到一个要求<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>并且需要验证失败以防止设置属性上不具有足够的安全性机制。 通过强制执行的 set-value 失效<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>还可能会禁止恶意调用方，如果应用程序域中运行这些调用方。  
  
## <a name="see-also"></a>请参阅

- [自定义依赖项属性](custom-dependency-properties.md)
