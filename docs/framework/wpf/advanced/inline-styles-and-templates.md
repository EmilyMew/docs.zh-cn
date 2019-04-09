---
title: 内联样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091429"
---
# <a name="inline-styles-and-templates"></a>内联样式和模板
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了<xref:System.Windows.Style>对象和模板对象 (<xref:System.Windows.FrameworkTemplate>子类) 作为一种方式在资源中定义的元素的可视外观，以便它们可以使用多次。 出于此原因中的属性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]采用类型<xref:System.Windows.Style>和<xref:System.Windows.FrameworkTemplate>几乎总是进行对现有样式和模板的资源引用而不是内联定义新的。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>内联样式和模板的限制  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，可以从技术上讲中两种方式之一设置样式和模板属性。 您可以使用特性语法引用已在其中定义资源，例如样式`<`*对象*`Style="{StaticResource`*myResourceKey*`}" .../>`。 或者，可以使用属性元素语法来定义内联样式，例如：  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 特性用法是更常见。 是以内联方式定义和未定义中资源的样式的一定范围限定为包含元素，且无法重新使用一样轻松因为它不有任何资源键。 一般情况下为资源定义的样式是更多情形且有用的并更符合一般原则是[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]编程模型将在代码中的程序逻辑分离从标记中的设计原则。  
  
 通常没有理由以设置内联样式或模板，即使只想要在该位置中使用该样式或模板。 可以采用的样式或模板的大多数元素还支持内容的属性和内容模型。 如果您仅使用任何逻辑树一次通过样式或模板创建，会更容易，只需直接标记中的等效子元素填充该内容属性。 这会完全跳过的样式和模板机制。  
  
 其他情况下，返回的对象标记扩展启用的语法也可使用的样式和模板。 有可能的方案的两个此类扩展包括[TemplateBinding](templatebinding-markup-extension.md)和<xref:System.Windows.Data.Binding>。  
  
## <a name="see-also"></a>请参阅

- [样式设置和模板化](../controls/styling-and-templating.md)
