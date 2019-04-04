---
title: 可区分联合
description: 了解如何使用F#可区分联合。
ms.date: 05/16/2016
ms.openlocfilehash: 9d3f423d068df1c43791919b0d71ca82304ae85e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821421"
---
# <a name="discriminated-unions"></a>可区分联合

可区分的联合提供的值可以为某个数量的已命名的情况下，可能是每个具有不同值和类型的支持。 可区分的联合可用于异类数据;可以具有特殊的情况下，包括有效和错误情况; 的数据在从一个实例到另一个; 的类型发生变化的数据和为小对象层次结构的替代方法。 此外，递归的可区分联合用于表示树数据结构。

## <a name="syntax"></a>语法

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>备注

可区分的联合类似于其他语言中的联合类型，但有差异。 作为使用 c + + 中的联合类型或在 Visual Basic 中的变量类型的值中存储的数据不被固定;它可以是若干个不同选项之一。 与这些其他语言中的联合不同，为每个可能的选项提供*用例标识符*。 用例标识符是有关此类型的对象可能是; 的值的各种可能的类型名称值是可选的。 如果值不存在，这种情况相当于枚举用例。 如果值存在，则每个值可以是单个值的指定的类型或聚合多个字段的相同或不同类型的元组。 可以为单个字段命名，但名称是可选的即使在相同情况下的其他字段的名称。

可区分联合可访问性默认为`public`。

例如，考虑形状类型的以下声明。

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

前面的代码声明的可区分的联合形状，它可以具有任意三个用例的值：矩形、 圆形和棱镜。 每种情况下具有一组不同的字段。 矩形用例有两个命名字段，这两个类型`float`，具有名称宽度和长度。 圆形用例都只是一个命名的字段，radius。 棱镜用例有三个字段，哪个 （宽度和高度） 的两个命名字段。 未命名的字段称为匿名字段。

通过根据以下示例的命名和匿名字段提供值来构造对象。

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

此代码显示了您可以使用命名的字段初始化，也可以依赖于声明中字段的排序方式，只需提供的值对于每个字段又。 有关构造函数调用`rect`前面的代码中使用的命名的字段，但对于构造函数调用`circ`使用了排序。 可以混合有序的字段和已命名字段，如下所示的构造`prism`。

`option`类型是一个简单的可区分的联合中F#核心库。 `option`类型声明，如下所示。

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

前面的代码中指定的类型`Option`是具有两种情况下，可区分的联合`Some`和`None`。 `Some`事例都有一个关联的值，其类型由类型参数的一个匿名字段组成`'a`。 `None`用例都没有关联的值。 因此`option`类型指定的泛型类型，既可以具有某些类型或任何值的值。 类型`Option`还具有小写的类型别名`option`，即更常用。

用例标识符可用作可区分联合类型的构造函数。 例如，使用以下代码创建的值`option`类型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

用例标识符还用在模式匹配表达式中。 在模式匹配表达式中，标识符提供了与各个用例关联的值。 例如，在下面的代码中，`x`标识符提供与相关联的值`Some`用例`option`类型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

在模式匹配表达式中，可以使用命名的字段来指定可区分的联合匹配。 对于以前声明的形状类型，可以使用命名的字段，如下面的代码所示，若要提取的字段的值。

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

通常情况下，用例标识符可以使用而无需对其进行联合的名称限定。 如果你想要始终用联合名称限定的名称，你可以申请[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)联合类型定义的属性。

### <a name="unwrapping-discriminated-unions"></a>解包的可区分的联合

在F#的可区分联合通常用于在域模型中包装单一类型。 它很容易提取通过模式匹配也的基础值。 您不需要对单个事例使用匹配表达式：

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

下面的示例演示这一操作：

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

模式匹配还允许直接在函数参数中，因此，可以解除单个事例的包装：

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>结构可区分联合

从F#4.1，您还可以表示为结构可区分联合。  这通过`[<Struct>]`属性。

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

因为这些是值类型，不能引用类型，所以一些额外注意事项与引用可区分联合：

1. 它们作为值类型复制，并具有值类型语义。
2. 不能用于 multicase 的结构可区分联合使用递归类型定义。
3. 必须提供 multicase struct 可区分联合的唯一大小写的名称。

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>使用可区分的联合替代对象层次结构

您可以通常可区分的联合用作小对象层次结构的更简单的替代。 无法为例，而不是使用以下可区分的联合`Shape`基类具有派生类型圆形、 方形，依此类推。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

而是虚方法来计算面积或周长，那样使用面向对象的实现中，可以使用模式匹配分支到合适的公式来计算这些数量。 在以下示例中，不同的公式用于计算区域，具体取决于该形状。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

输出如下所示：

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>对树数据结构使用可区分的联合

可区分的联合可以是递归的这意味着联合本身，可以包含在一个或多个用例的类型。 递归的可区分的联合可用于创建树的结构，用于记录的编程语言中的模型表达式。 在下面的代码中，递归的可区分联合用于创建二进制树数据结构。 该联合的两种情况，包括`Node`，这是一个包含一个整数值和左、 右子树节点和`Tip`，后者用于终结树。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

在前面的代码，`resultSumTree`具有值 10。 下图显示的树结构`myTree`。

![图，显示 mytree 的树结构。](../media/discriminated-unions/tree-structure-mytree.png)

如果在树中的节点是异类是可行的可区分的联合。 在下面的代码中，类型`Expression`表示一种简单的编程语言支持添加中的表达式的抽象语法树和乘法的数字和变量。 一些联合用例不是递归的表示数字 (`Number`) 或变量 (`Variable`)。 其他情况下是递归的并表示操作 (`Add`和`Multiply`)、 的操作数也是表达式。 `Evaluate`函数使用匹配表达式以递归方式处理语法树。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

此代码执行时，值`result`为 5。

## <a name="common-attributes"></a>通用属性

以下属性是可区分联合中经常见到：

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)