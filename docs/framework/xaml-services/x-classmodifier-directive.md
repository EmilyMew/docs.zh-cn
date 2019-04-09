---
title: x:ClassModifier 指令
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: fdbc69634e86992e71cfccdc080829b6b45f963c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100910"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier 指令
修改 XAML 编译行为时`x:Class`还提供了。 具体而言，而不是创建一个分部`class`，其`Public`访问级别 （默认值），提供`x:Class`使用创建`NotPublic`访问级别。 此行为会影响生成的程序集中类的访问级别。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*NotPublic*|确切的字符串传递的用于指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>与<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>各不相同，具体取决于您使用的代码隐藏编程语言。 请参阅“备注”。|  
  
## <a name="dependencies"></a>依赖项  
 [x： 类](x-class-directive.md)还必须提供在同一元素上并且该元素必须是一个页面中的根元素。 有关详细信息，请参阅[ \[MS XAML\]部分 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="remarks"></a>备注  
 值`x:ClassModifier`.NET Framework XAML 服务中而异的编程语言的使用情况。 要使用的字符串取决于如何实现每种语言及其<xref:System.CodeDom.Compiler.CodeDomProvider>和类型转换器，它将返回定义的含义<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及该语言是否区分大小写。  
  
-   对于 C#，要传递的用于指定的字符串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`internal`。  
  
-   用于 Microsoft Visual Basic.NET，要传递的用于指定的字符串<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是`Friend`。  
  
-   有关[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，没有目标存在支持编译 XAML 的; 因此，未指定要传递的值。  
  
 此外可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>(`public`在 C# 中，`Public`在 Visual Basic 中); 但是，指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>很少做是因为<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已经是默认行为。  
  
 其他值，相当的用户代码访问级别的限制，如`private`在 C# 中，不是适用于`x:ClassModifier`因为 XAML，不支持嵌套的类的引用，因此，<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修饰符具有相同的效果。  
  
## <a name="security-notes"></a>安全说明  
 中声明的访问级别`x:ClassModifier`仍取决于特定的框架和及其功能的解释。 WPF 还包括加载和实例化类型的功能，`x:ClassModifier`是`internal`，如果该类从 WPF 资源通过 URI 引用的包引用。 这种情况下以及可能其他类似的其他框架实现，因此不要依赖于以独占方式在`x:ClassModifier`来阻止所有可能实例化尝试。  
  
## <a name="see-also"></a>请参阅

- [x:Class 指令](x-class-directive.md)
- [WPF 中的代码隐藏和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier 指令](x-fieldmodifier-directive.md)
- [安全性 (WPF)](../wpf/security-wpf.md)
- [从 WPF 迁移到 System.Xaml 的类型](types-migrated-from-wpf-to-system-xaml.md)
