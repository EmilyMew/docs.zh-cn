---
title: mc:ProcessContent 特性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 865b1a3ccc30ff5efab4b08956bf7ba2bba4769c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110581"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 特性
指定哪些[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]元素仍应具有处理相关的父元素的内容，即使可能忽略的直接父元素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]由于指定的处理器[mc: Ignorable 特性](mc-ignorable-attribute.md). `mc:ProcessContent`属性支持标记兼容性，对自定义的命名空间映射以及[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]版本控制。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*ignorablePrefix*|任何有效的前缀字符串，每个 XML 1.0 规范。|  
|*ignorableUri*|任何有效的 URI 指定一个命名空间，每个 XML 1.0 规范。|  
|*ThisElementCanBeIgnored*|元素，可以忽略[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]处理器实现中，如果基础类型不能被解析。|  
|*[content]*|*ThisElementCanBeIgnored*被标记为可忽略。 如果处理器忽略该元素， *[内容]* 由处理*对象*。|  
  
## <a name="remarks"></a>备注  
 默认情况下，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器将忽略已忽略元素中的内容。 可以指定特定元素由`mc:ProcessContent`，和一个[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]处理器将继续处理中忽略了元素的内容。 这通常可在内容嵌套在多个标记，在至少一个可以忽略，并在至少一个不被可忽略。  
  
 可以使用空间分隔符，例如在特性中指定多个前缀： `mc:ProcessContent="ignore:Element1 ignore:Element2"`。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]命名空间定义其他元素和属性的未记录的此区域内[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]。 有关详细信息，请参阅[XML 标记兼容性规范](https://go.microsoft.com/fwlink/?LinkId=73824)。  
  
## <a name="see-also"></a>请参阅

- [mc:Ignorable 特性](mc-ignorable-attribute.md)
- [XAML 概述 (WPF)](xaml-overview-wpf.md)
