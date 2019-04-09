---
title: 导入声明：Open 关键字
description: 了解如何F#导入声明和如何指定模块或命名空间可以不使用完全限定的名称引用其中的元素。
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59054996"
---
# <a name="import-declarations-the-open-keyword"></a>导入声明：`open`关键字

> [!NOTE]
> 本文中的 API 参考链接将转至 MSDN。  Docs.microsoft.com API 参考尚未完成。

*导入声明*指定模块或命名空间可以不使用完全限定的名称引用其中的元素。

## <a name="syntax"></a>语法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>备注

使用完全限定的命名空间或模块路径来引用代码每次都可以创建很难编写、 读取和维护的代码。 相反，可以使用`open`关键字常用模块和命名空间，以便在引用该模块或命名空间的成员时，您可以使用名称的缩写形式而不是完全限定名称。 此关键字是类似于`using`关键字在 C# 中， `using namespace` Visual c + +，和`Imports`在 Visual Basic 中。

模块或命名空间提供必须在同一项目中或在引用的项目或程序集中。 如果不是这样，可以添加到项目中，引用或使用`-reference`命令`-`行选项 (或其缩写， `-r`)。 有关详细信息，请参阅[编译器选项](compiler-options.md)。

导入声明使这些名称可以在下面的声明，直至封闭命名空间、 模块或文件的末尾的代码。

当使用多个导入声明时，它们应显示在单独的行上。

下面的代码演示如何使用`open`关键字来简化代码。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F#多个打开的模块或命名空间中出现相同的名称时，会出现多义性时，编译器不会发出错误或警告。 当出现多义性问题时，F#提供了对更多最近打开的模块或命名空间的首选项。 例如，在下面的代码中，`empty`意味着`Seq.empty`，即使`empty`位于在这种`List`和`Seq`模块。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此，要小心，如打开模块或命名空间时`List`或`Seq`包含具有相同的名称; 相反，可考虑使用限定的名称的成员。 应避免任何情况下，在其中的代码是依赖于导入声明的顺序。

## <a name="namespaces-that-are-open-by-default"></a>默认情况下打开的命名空间

一些命名空间相当频繁，因此可在F#而无需显式导入声明它们也隐式打开的代码。 下表显示了默认情况下打开的命名空间。

|命名空间|描述|
|---------|-----------|
|`Microsoft.FSharp.Core`|包含基本F#类型的内置类型定义，如`int`并`float`。|
|`Microsoft.FSharp.Core.Operators`|包含基本算术运算，如`+`和`*`。|
|`Microsoft.FSharp.Collections`|包含不可变集合类，例如`List`和`Array`。|
|`Microsoft.FSharp.Control`|包含用于控制构造，如惰性计算和异步工作流类型。|
|`Microsoft.FSharp.Text`|包含函数格式化 io，如`printf`函数。|

## <a name="autoopen-attribute"></a>AutoOpen 特性

您可以将应用`AutoOpen`属性对程序集，如果你想要引用的程序集时自动打开命名空间或模块。 您还可以应用`AutoOpen`要打开的父模块或命名空间时自动打开该模块的模块的属性。 有关详细信息，请参阅[Core.AutoOpenAttribute 类](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 特性

某些模块、 记录或联合类型可指定`RequireQualifiedAccess`属性。 在引用这些模块、 记录或联合中的元素时，必须使用而不考虑是否包括导入声明的限定的名称。 如果使用此属性有策略地进行上通常定义的类型使用的名称，帮助避免发生名称冲突，从而使代码更具弹性库中的更改。 有关详细信息，请参阅[Core.RequireQualifiedAccessAttribute 类](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
- [命名空间](namespaces.md)
- [模块](modules.md)
