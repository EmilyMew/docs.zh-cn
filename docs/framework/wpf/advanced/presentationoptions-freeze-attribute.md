---
title: PresentationOptions:Freeze 特性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074652"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 特性
集<xref:System.Windows.Freezable.IsFrozen%2A>状态变为`true`上包含<xref:System.Windows.Freezable>元素。 默认行为<xref:System.Windows.Freezable>而无需`PresentationOptions:Freeze`指定的属性是<xref:System.Windows.Freezable.IsFrozen%2A>是`false`加载时间和依赖于一般<xref:System.Windows.Freezable>在运行时的行为。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`PresentationOptions`|XML 命名空间前缀，这可以是任何有效的前缀字符串，每个 XML 1.0 规范。 前缀`PresentationOptions`用于标识此文档中使用。|  
|`freezableElement`|实例化任何元素派生的类<xref:System.Windows.Freezable>。|  
  
## <a name="remarks"></a>备注  
 `Freeze`属性是唯一的属性或其他编程元素中定义`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`XML 命名空间。 `Freeze`具体来说，以便可以将其指定为可忽略，使用此特殊的命名空间中存在的属性[mc: Ignorable 特性](mc-ignorable-attribute.md)作为根元素声明的一部分。 原因，`Freeze`必须是可以忽略是因为并非所有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器实现可冻结<xref:System.Windows.Freezable>在加载时; 此功能不是属于[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]规范。  
  
 处理的能力`Freeze`属性专门的内置[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器，用于处理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]为编译的应用程序。 该属性不受任何类和属性语法不可扩展或可修改。 如果要实现您自己[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器可以选择并行的冻结行为[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器处理时`Freeze`特性，可以在<xref:System.Windows.Freezable>在加载时的元素。  
  
 任何值`Freeze`特性，除`true`（不区分大小写） 生成的负载时错误。 (指定`Freeze`属性作为`false`不是错误，但这已经是默认值，因此将设置为`false`不执行任何操作)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Freezable>
- [Freezable 对象概述](freezable-objects-overview.md)
- [mc:Ignorable 特性](mc-ignorable-attribute.md)
