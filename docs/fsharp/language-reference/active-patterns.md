---
title: 活动模式
description: 了解如何使用活动模式以定义细分输入的数据中的命名的分区F#编程语言。
ms.date: 05/16/2016
ms.openlocfilehash: 0f1f57de425836738201d2d8f84ab67a0df142ee
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412079"
---
# <a name="active-patterns"></a>活动模式

*活动模式*使您能够定义细分输入的数据的已命名的分区，以便可以在模式匹配表达式，就像可区分联合使用这些名称。 可使用活动模式以自定义方式为每个分区分解数据。

## <a name="syntax"></a>语法

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>备注

在上述语法中，标识符是由表示的输入数据的分区的名称*自变量*，或者，换而言之，子集的所有值的参数集的名称。 活动的模式定义中可以有最多七个分区。 *表达式*描述要将数据分解到的窗体。 活动的模式定义可用于定义用于确定哪些已命名分区根据参数属于给定的值的规则。 (| 和 |) 符号嘿*香蕉夹*并创建此类型的 let 绑定的函数调用*活动的识别器*。

作为示例，请考虑以下活动的模式的参数。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

在模式匹配表达式，如以下示例所示，可以使用活动的模式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

此程序的输出如下所示：

```
7 is odd
11 is odd
32 is even
```

活动模式的另一个用途是将分解在多个方面，例如当同一基础数据具有各种可能的表示形式的数据类型。 例如，`Color`对象无法分解为一表示形式，RGB 或 HSB 表示形式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上面的程序中的输出如下所示：

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

结合使用，这两种方式使用活动模式的分区，您将数据分解为适当的形式为和最方便的计算窗体中的相应数据执行适当的计算。

生成的模式匹配表达式使数据能够编写得非常易读，极大地简化了潜在的复杂分支和数据分析代码的简便方式。

## <a name="partial-active-patterns"></a>部分活动模式

有时，您需要进行分区仅输入空间的一部分。 在这种情况下，您编写一组的部分模式，其中匹配一些输入，但无法匹配其他输入。 始终不会生成值的活动模式被称为*分部活动模式*; 它们具有返回值将是选项类型。 若要定义部分活动模式，您可以使用通配符字符 (\_) 模式在香蕉夹内的列表的末尾。 下面的代码演示如何使用部分活动模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

上一示例的输出如下所示：

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

当使用部分活动模式时，有时单项选择可以是不连续或互斥的但它们不需要。 在以下示例中，模式正方形和多维数据集的模式不是连续的因为一些数字是平方和多维数据集，例如 64。 以下程序使用 AND 模式合并的正方形和立方体的模式。 它打印最大 1000 是同时平方和多维数据集，以及是只有多维数据集的所有整数。 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

输出如下所示：

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>参数化活动模式

活动模式始终采用至少一个参数为要匹配的项，但也可能会采用其他参数，这种情况下名称*参数化活动模式*适用。 其他参数，可进行专用化的常规模式。 例如，使用正则表达式分析字符串通常的活动模式包括正则表达式作为一个额外的参数，如下面的代码，还会使用部分活动模式中所示`Integer`在前面的代码示例中定义。 在此示例中，提供有关各种日期格式中使用正则表达式的字符串以自定义常规 ParseRegex 活动模式。 使用整数活动模式以匹配的字符串转换为可传递给 DateTime 构造函数的整数。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

上述代码的输出如下所示：

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

活动模式不会限制仅用于模式匹配表达式，也可以让绑定上使用它们。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

上述代码的输出如下所示：

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
- [match 表达式](match-expressions.md)
