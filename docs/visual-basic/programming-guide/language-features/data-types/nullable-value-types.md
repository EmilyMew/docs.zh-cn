---
title: 可以为 null 值类型的 Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921307"
---
# <a name="nullable-value-types-visual-basic"></a>可以为 Null 的值类型 (Visual Basic)

有时，你将使用在某些情况下没有已定义的值的值类型。 例如，在数据库中的字段可能需要区分具有分配的值有意义的而不让分配的值。 值类型可以扩展以使其正常值或 null 值。 调用此类扩展*为 null 的类型*。

每个可以为 null 的类型从泛型构造<xref:System.Nullable%601>结构。 假设有一个数据库，用于跟踪与工作相关的活动。 下面的示例构造一个可以为 null`Boolean`类型，并声明该类型的变量。 以下三种方式，可以编写以下声明：

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

在变量`ridesBusToWork`可以保存的值`True`，值为`False`，或者根本没有值。 其初始默认值是没有值，这在此情况下可能意味着，信息具有尚未获得此人。 与此相反，`False`可能是获得的信息，而该人员未乘坐公共汽车去上班。

可以使用可以为 null 的类型来声明变量和属性，并可以声明具有可以为 null 的类型的元素的数组。 可以使用作为参数，可以为 null 的类型来声明过程和可以返回 null 的类型从`Function`过程。

无法构造为 null 的类型，如数组、 引用类型上`String`，或类。 基础类型必须是值类型。 有关更多信息，请参见 [Value Types and Reference Types](value-types-and-reference-types.md)。

## <a name="using-a-nullable-type-variable"></a>使用可以为 Null 的类型变量

可以为 null 的类型的最重要成员是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>属性。 变量的为 null 的类型，<xref:System.Nullable%601.HasValue%2A>告诉您此变量是否包含定义的值。 如果<xref:System.Nullable%601.HasValue%2A>是`True`，你可以读取的值从<xref:System.Nullable%601.Value%2A>。 请注意，这两<xref:System.Nullable%601.HasValue%2A>并<xref:System.Nullable%601.Value%2A>是`ReadOnly`属性。

### <a name="default-values"></a>默认值

使用可以为 null 的类型和声明变量时其<xref:System.Nullable%601.HasValue%2A>属性具有默认值为`False`。 这意味着默认情况下该变量具有未定义的值，而不是其基础值类型的默认值。 在下面的示例中，变量`numberOfChildren`最初有没有定义的值，即使的默认值`Integer`类型为 0。

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Null 值可用于指示未定义或未知值。 如果`numberOfChildren`已声明为`Integer`，会有任何可能表示信息不是当前可用的值。

### <a name="storing-values"></a>将值存储

以典型方式，可以在变量或可以为 null 的类型的属性中存储值。 下面的示例将一个值分配给变量`numberOfChildren`上一示例中声明。

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

如果变量或可以为 null 的类型的属性包含已定义的值，则可以使此恢复到其初始状态不具有分配的值。 为此，可设置的变量或属性设置为`Nothing`，如下面的示例所示。

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> 尽管可以将分配`Nothing`不能为 null 的类型的变量，测试其用于`Nothing`使用等号。 使用等号的比较`someVar = Nothing`，计算结果始终为`Nothing`。 你可以测试的变量<xref:System.Nullable%601.HasValue%2A>属性`False`，或使用测试`Is`或`IsNot`运算符。

### <a name="retrieving-values"></a>检索值

若要检索的可以为 null 的类型的变量的值，应该首先测试其<xref:System.Nullable%601.HasValue%2A>属性来确认它具有值。 如果您尝试读取值时<xref:System.Nullable%601.HasValue%2A>是`False`，Visual Basic 将引发<xref:System.InvalidOperationException>异常。 下面的示例演示读取该变量的建议的方法`numberOfChildren`的前面的示例。

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>可以为 Null 的类型比较

可以为 null 时`Boolean`在布尔表达式中使用变量，结果可以是`True`， `False`，或`Nothing`。 下面是真值表`And`和`Or`。 因为`b1`和`b2`现在有三个可能值有九个组合来评估。

|b1|b2|b1 和 b2|b1 或 b2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

当布尔型变量或表达式的值是`Nothing`，它既不是`true`也不`false`。 请看下面的示例。

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

在此示例中，`b1 And b2`计算结果为`Nothing`。 因此，`Else`子句中每个执行`If`语句，并输出如下所示：

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` 并`OrElse`，可使用该技术短路计算，必须评估其第二个操作数时第一个计算结果为`Nothing`。

## <a name="propagation"></a>传播

如果一个或两个操作数的算术、 比较、 shift 键或类型操作可以为 null，该操作的结果也是可以为 null。 如果两个操作数的值`Nothing`，对底层的操作数，值执行此操作，因为如果它们都不是 null 的类型。 在下面的示例中，变量`compare1`和`sum1`隐式类型化。 如果将鼠标指针停留在其上时，将看到编译器将为 null 的类型推断为这两个值。

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

如果一个或两个操作数具有值为`Nothing`，结果将是`Nothing`。

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>数据中使用可以为 Null 的类型

数据库是一个最重要的地方使用可以为 null 的类型。 并非所有数据库对象当前都支持可以为 null 的类型，但设计器生成的表适配器。 请参阅[为 null 的类型的 TableAdapter 支持](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)。

## <a name="see-also"></a>请参阅

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [使用可以为 null 的类型](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [数据类型](index.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [数据类型疑难解答](troubleshooting-data-types.md)
- [使用 Tableadapter 填充数据集](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If 运算符](../../../language-reference/operators/if-operator.md)
- [局部类型推理](../variables/local-type-inference.md)
- [Is 运算符](../../../language-reference/operators/is-operator.md)
- [IsNot 运算符](../../../language-reference/operators/isnot-operator.md)