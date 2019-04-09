---
title: x:TypeArguments 指令
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 1d1b10b4da1263843bdce5447f0716569c7700e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085800"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指令
约束类型参数传递给泛型类型的构造函数的泛型。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`object`|由 CLR 泛型类型提供支持的 XAML 类型的对象元素声明。 如果`object`不是默认 XAML 命名空间中的 XAML 类型是指`object`需要一个指示 XAML 命名空间前缀其中`object`存在。|  
|`typeString`|一个字符串，声明一个或多个 XAML 类型名称以字符串形式提供的类型参数的 CLR 泛型类型。 有关其他语法说明，请参阅备注。|  
  
## <a name="remarks"></a>备注  
 在大多数情况下，为信息项中使用的 XAML 类型`typeString`字符串作为前缀。 典型类型的 CLR 的泛型约束 (例如，<xref:System.Int32>和<xref:System.String>) 来自 CLR 基类库。 这些库不映射到典型的特定于框架的默认 XAML 命名空间，因此，对于 XAML 使用情况需要前缀映射。  
  
 可以通过使用逗号分隔符指定多个 XAML 类型名称。  
  
 如果泛型约束自身使用的泛型类型，括号 （） 可以包含嵌套的约束类型参数。  
  
 请注意，此定义的`x:TypeArguments`是特定于.NET Framework XAML 服务和使用 CLR 支持。 可以在中找到的语言级别定义[ \[MS XAML\]部分 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="usage-examples"></a>用法示例  
 对于这些示例，假定声明以下 XAML 命名空间定义：  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>列表\<字符串 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 实例化新<xref:System.Collections.Generic.List%601>与<xref:System.String>类型实参。  
  
### <a name="dictionarystringstring"></a>字典\<字符串、 字符串 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 实例化新<xref:System.Collections.Generic.Dictionary%602>具有两个<xref:System.String>类型参数。  
  
### <a name="queuekeyvaluepairstringstring"></a>队列 < KeyValuePair\<String，String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 实例化新<xref:System.Collections.Generic.Queue%601>具有的约束<xref:System.Collections.Generic.KeyValuePair%602>内部约束类型参数与<xref:System.String>和<xref:System.String>。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF 泛型 XAML 用法  
 有关 XAML 2006 使用情况和 XAML 的 WPF 应用程序使用，存在以下限制`x:TypeArguments`和从 XAML 中常规的泛型类型用法：  
  
-   XAML 文件的根元素可以支持引用泛型类型的泛型 XAML 用法。  
  
-   根元素必须映射到具有至少一个类型参数的泛型类型。 例如， <xref:System.Windows.Navigation.PageFunction%601>。 页函数是 XAML 在 WPF 中的泛型用法支持的主要方案。  
  
-   泛型的根元素 XAML 对象元素还必须声明分部类使用`x:Class`。 即使定义 WPF 生成操作，这是如此。  
  
-   `x:TypeArguments` 不能引用嵌套的泛型约束。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 或不带任何 WPF 3.0 或 3.5 WPF XAML 2006 依赖关系  
 在.NET Framework XAML 服务 XAML 2006 或 XAML 2009，放宽了对泛型的 XAML 用法的 WPF 相关限制。 您可以实例化泛型对象元素，在后备类型系统和对象模型可以支持的 XAML 标记中的任意位置。  
  
 如果使用 XAML 2009 而不是将 CLR 映射基类型来获取常用语言基元的 XAML 类型转换，则可以使用[常见 XAML 语言基元的内置类型](built-in-types-for-common-xaml-language-primitives.md)中的信息项作为`typeString`。 例如，您可以声明以下 （前缀映射不显示，但 x 是 XAML 2009 的 XAML 语言 XAML 命名空间）：  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中并面向[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，可以使用 XAML 2009 功能一起使用`x:TypeArguments`但只针对松散 XAML (未标记编译的 XAML)。 WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。 如果需要为标记编译 XAML，您必须在"XAML 2006 和 WPF 泛型 XAML 用法"部分中所述的限制下进行操作。  
  
## <a name="see-also"></a>请参阅

- [x:Class 指令](x-class-directive.md)
- [x:Type 标记扩展](x-type-markup-extension.md)
- [常见 XAML 语言基元的内置类型](built-in-types-for-common-xaml-language-primitives.md)
- [XAML 中的泛型](generics-in-xaml.md)
