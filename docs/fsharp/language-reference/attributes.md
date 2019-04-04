---
title: 特性
description: 了解如何F#属性启用要应用于编程构造的元数据。
ms.date: 05/16/2016
ms.openlocfilehash: 6e80bc4e32ee4ff5ff132270bde8e2fd018369e1
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464653"
---
# <a name="attributes"></a>特性

属性启用要应用于编程构造的元数据。

## <a name="syntax"></a>语法

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>备注

在上述语法中，*目标*是可选的并且如果存在，则指定特性所应用到程序实体的类型。 有效值*目标*出现在本文档后面的表中所示。

*属性名称*引用 （可能是用命名空间限定） 名称的有效的特性类型，带有或不带后缀`Attribute`的常用属性的类型名称。 例如，类型`ObsoleteAttribute`可以缩短至只有`Obsolete`在此上下文中。

*自变量*是属性类型构造函数的参数。 如果属性具有默认构造函数，可以省略参数列表和括号。 属性支持位置参数和命名自变量。 *位置参数*是它们的显示的顺序中使用的参数。 如果属性具有公共属性，可以使用命名的参数。 您可以设置这些自变量列表中使用以下语法。

```
*property-name* = *property-value*
```

此类属性初始化可以任何顺序，但它们必须遵循任何位置自变量。 下面是使用位置自变量和属性初始化属性的一个示例。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

在此示例中，属性是`DllImportAttribute`，此处使用缩写形式。 第一个参数是位置参数和第二个是一个属性。

属性是.NET 编程构造，使对象称为*特性*要与类型或其他程序元素相关联。 特性应用于程序元素称为*属性目标*。 该属性通常包含有关其目标的元数据。 在此上下文中，元数据可能是其字段和成员以外的类型有关的任何数据。

中的属性F#可应用于以下的编程构造： 函数、 方法、 程序集、 模块、 类型 （类、 记录、 结构、 接口、 委托、 枚举、 联合和等等）、 构造函数、 属性、 字段，参数，类型参数，并返回值。 属性不允许对`let`类、 表达式或工作流表达式内部的绑定。

通常情况下，特性声明的属性目标的声明之前直接显示。 可以使用多个属性声明，在一起，按如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

可以通过使用.NET 反射在运行时查询属性。

如前面的代码示例中所示，声明单独，多个属性，或如果您使用分号来分隔各个属性和构造函数，如下所示可以声明它们中一组方括号。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

通常会遇到的属性包括`Obsolete`COM 支持、 与代码中，所有权相关的属性和属性，指示是否可以序列化类型的属性，出于安全考虑，特性属性。 下面的示例演示如何将`Obsolete`属性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

对于特性目标`assembly`并`module`，将特性应用于顶级`do`中您的程序集的绑定。 可以包括词`assembly`或`module`在属性声明中，按如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

如果忽略应用于的特性的属性目标`do`绑定，F#编译器将尝试确定该属性有意义的属性目标。 许多属性类具有类型的属性`System.AttributeUsageAttribute`，包括支持该属性的可能目标有关的信息。 如果`System.AttributeUsageAttribute`指示该属性支持使用函数作为目标，则会特性要应用于程序的主入口点。 如果`System.AttributeUsageAttribute`指示该属性支持使用作为目标的程序集，编译器会将特性应用于程序集。 大多数属性不适用于函数和程序集，但在完成的情况下，会将特性应用于程序的主函数。 如果显式指定特性目标，则该属性应用到指定的目标。

尽管您通常不必指定特性显式目标的有效值*目标*在属性中所示下表中，以及使用情况的示例。

<table>
  <tr>
    <th>属性目标</td>
    <th>示例</td> 
  </tr>
  <tr>
    <td>程序集</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td>Field — 字段</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td>属性</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
  </tr>
  <tr>
    <td>类型</td>
    <td>
        <pre lang="fsharp"><code>
        [&lt;type: StructLayout(Sequential)&gt;] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)