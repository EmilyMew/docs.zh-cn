---
title: 显式字段：Val 关键字
description: 了解如何F#值关键字用于声明类或结构类型中存储一个值，而不初始化该类型的位置。
ms.date: 05/16/2016
ms.openlocfilehash: 6557514f13a9e86c7f367713775535db79e99a0c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634006"
---
# <a name="explicit-fields-the-val-keyword"></a>显式字段：Val 关键字

`val` 关键字用于声明在类或结构类型中存储一个值（但不初始化该值）的位置。 在这种方式中声明的存储位置称为*显式字段*。 `val` 关键字的另一个用法是结合 `member` 关键字来声明一个自动实现的属性。 有关自动实现的属性的详细信息，请参阅[属性](properties.md)。

## <a name="syntax"></a>语法

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>备注

在类或结构类型中定义字段的通常方式是使用 `let` 绑定。 但是，`let` 绑定必须初始化为类构造函数的一部分，而这并不总是可能、有必要或必需实现的。 当你需要一个未初始化的字段时，可以使用 `val` 关键。

显式字段可以为静态或非静态的。 *访问修饰符*可以是`public`， `private`，或`internal`。 默认情况下，显式字段是公共的。 这不同于类中的 `let` 绑定，后者始终是私有的。

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58)需要在具有主构造函数的类类型中的显式字段上设置属性。 此特性指定该字段被初始化为零。 字段的类型必须支持零初始化。 如果一个类型为以下类型之一，则该类型支持零初始化：

- 具有零值的基元类型。

- 一种支持 Null 值作为标准值、异常值或值表示形式的类型。 这包括类、元组、记录、函数、接口、.NET 引用类型、`unit` 类型以及可区分联合类型。

- 一个 .NET 值类型。

- 一种结构，其字段均支持默认值零。

例如，称为 `someField` 的不可变字段具有一个 .NET 编译表示形式的支持字段，该字段名为 `someField@`，你可以使用名为 `someField` 的属性访问存储值。

对于可变字段，.NET 编译的表示形式是一个 .NET 字段。

>[!WARNING]
>.NET Framework 命名空间`System.ComponentModel`包含具有相同名称的属性。 有关该属性的信息，请参见 `System.ComponentModel.DefaultValueAttribute`。

以下代码展示了显式字段的用法，作为对比，还展示了具有主构造函数的类中的 `let` 绑定。 注意：与 `let` 字段绑定的 `myInt1` 是私有的。 当从成员方法引用与 `let` 字段绑定的 `myInt1` 时，不需要自我标识符 `this`。 但如果要引用显式字段 `myInt2` 和 `myString`，则需要自我标识符。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

输出如下所示：

```
11 12 abc
30 def
```

以下代码展示了不具有主构造函数的类中的显式字段的用法。 在该例中，不需要 `DefaultValue` 特性，但所有字段必须在为该类型定义的构造函数中进行初始化。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

输出为 `35 22`。

以下代码展示了结构中显式字段的用法。 由于结构是值类型，它自动具有默认构造函数，该函数将其字段的值设置为零。 因此，不需要 `DefaultValue` 特性。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

输出为 `11 xyz`。

**请注意**，如果要初始化您的结构与`mutable`字段而无需`mutable`关键字，将工作分配给您的结构，它将被放弃之后立即分配的副本上。 因此不会更改您的结构。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

显式字段不适用于例程使用。 通常，在可能的情况下，应在类中使用 `let` 绑定，而不是显式字段。 显式字段在某些互操作性方案中十分有用，例如，当需要定义一个结构，该结构将用在对本机 API 的平台调用中，或用在 COM 互操作方案中。 有关详细信息，请参阅[外部函数](../functions/external-functions.md)。 另一种要用到显式字段的情况是当使用 F# 代码生成器时，该生成器会发出不具有主构造函数的类。 显式字段对于线程静态变量或类似的构造而言也十分有用。 有关详细信息，请参阅 `System.ThreadStaticAttribute`。

当关键字 `member val` 在一个类型定义中同时出现，它就是一个自动实现属性的定义。 有关更多信息，请参见 [属性](properties.md)中定义的接口的私有 C++ 特定实现。

## <a name="see-also"></a>请参阅

- [属性](properties.md)
- [成员](index.md)
- [类中的 `let` 绑定](let-bindings-in-classes.md)
