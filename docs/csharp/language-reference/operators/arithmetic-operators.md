---
title: 算术运算符 - C# 参考
description: 了解对数值类型执行乘法、除法、余数、加法和减法运算的 C# 运算符。
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: 192acf6fea0c6014aaf092077f8deaa844dfd2ec
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633798"
---
# <a name="arithmetic-operators-c-reference"></a>算术运算符（C# 参考）

以下运算符对数值类型执行算术运算：

- 一元 [`++`（增量）](#increment-operator-)、[`--`（减量）](#decrement-operator---)、[`+`（加）](#unary-plus-and-minus-operators) 和 [`-`（减）](#unary-plus-and-minus-operators)运算符。
- 二元 [`*`（乘）](#multiplication-operator-)[`/`（除）](#division-operator-)[`%`（余数）](#remainder-operator-)[`+`（加）](#addition-operator-) 和 [`-`（减）](#subtraction-operator--) 运算符。

这些运算符支持所有[整型](../keywords/integral-types-table.md)和[浮动](../keywords/floating-point-types-table.md)数值类型。

## <a name="increment-operator-"></a>增量运算符 ++

一元增量运算符 `++` 按 1 递增其操作数。 操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)访问或[索引器](../../../csharp/programming-guide/indexers/index.md)访问。

增量运算符以两种形式进行支持：后缀增量运算符 `x++` 和前缀增量运算符 `++x`。

### <a name="postfix-increment-operator"></a>后缀递增运算符

`x++` 的结果是此操作前的 `x` 的值，如以下示例所示：

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>前缀增量运算符

`++x` 的结果是此操作后的 `x` 的值，如以下示例所示：

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>减量运算符 --

一元减量运算符 `--` 按 1 递减其操作数。 操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)访问或[索引器](../../../csharp/programming-guide/indexers/index.md)访问。

减量运算符以两种形式进行支持：后缀减量运算符`x--` 和前缀减量运算符 `--x`。

### <a name="postfix-decrement-operator"></a>后缀递减运算符

`x--` 的结果是此操作前的 `x` 的值，如以下示例所示：

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>前缀减量运算符

`--x` 的结果是此操作后的 `x` 的值，如以下示例所示：

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>一元加和减运算符

一元 `+` 运算符返回其操作数的值。 一元 `-` 运算符对其操作数的数值取负。

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

一元 `-` 运算符不支持 [ulong](../keywords/ulong.md) 类型。

## <a name="multiplication-operator-"></a>乘法运算符 *

乘法运算符 `*` 计算其操作数的乘积：

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

一元 `*` 运算符是[指针间接运算符](multiplication-operator.md#pointer-indirection-operator)。

## <a name="division-operator-"></a>除法运算符 /

除法运算符 `/` 用它的第一个操作数除以第二个操作数。

### <a name="integer-division"></a>整数除法

对于整数类型的操作数，`/` 运算符的结果为整数类型，并且等于两个操作数之商向零舍入后的结果：

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

若要获取浮点数形式的两个操作数之商，请使用 `float`、`double` 或 `decimal` 类型：

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>浮点除法

对于 `float`、`double` 和 `decimal` 类型，`/` 运算符的结果为两个操作数之商：

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

如果操作数之一为 `decimal`，那么另一个操作数不得为 `float` 和 `double`，因为 `float` 和 `double` 都无法隐式转换为 `decimal`。 必须将 `float` 或 `double` 操作数显式转换为 `decimal` 类型。 若要详细了解数值类型之间的隐式转换，请参阅[隐式数值转换表](../keywords/implicit-numeric-conversions-table.md)。

## <a name="remainder-operator-"></a>余数运算符 %

余数运算符 `%` 计算第一个操作数除以第二个操作数后的余数。

### <a name="integer-remainder"></a>整数余数
  
对于整数类型的操作数，`a % b` 的结果是 `a - (a / b) * b` 得出的值。 非零余数的符号与第一个操作数的符号相同，如下例所示：

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

使用 <xref:System.Math.DivRem%2A?displayProperty=nameWithType> 方法计算整数除法和余数结果。

### <a name="floating-point-remainder"></a>浮点余数

对于 `float` 和 `double` 操作数，有限的 `x` 和 `y` 的 `x % y` 的结果是值 `z`，因此

- `z`（如果不为零）的符号与 `x` 的符号相同。
- `z` 的绝对值是 `|x| - n * |y|` 得出的值，其中 `n` 是小于或等于 `|x| / |y|` 的最大可能整数，`|x|` 和 `|y|` 分别是 `x` 和 `y` 的绝对值。

> [!NOTE]
> 计算余数的此方法类似于用于整数操作数的方法，但与 IEEE 754 不同。 如果需要符合 IEEE 754 的余数运算，使用 <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 方法。

有关非限定操作数的 `%` 运算符行为的信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[余数运算符](~/_csharplang/spec/expressions.md#remainder-operator)章节。

对于 `decimal` 操作数，余数运算符 `%` 等效于 <xref:System.Decimal?displayProperty=nameWithType> 类型的[余数运算符](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。

以下示例演示了具有浮动操作数的余数运算符的行为：

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>加法运算符 +

加法运算符 `+` 计算其操作数的和。

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

还可以将 `+` 运算符用于字符串串联和委托组合。 有关详细信息，请参阅[`+`运算符](addition-operator.md)一文。

## <a name="subtraction-operator--"></a>减法运算符 -

减法运算符 `-` 从其第一个操作数中减去其第二个操作数：

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

还可以使用 `-` 运算符删除委托。 有关详细信息，请参阅[`-`运算符](subtraction-operator.md)一文。

## <a name="operator-precedence-and-associativity"></a>运算符优先级和关联性

以下列表对优先级由高到低的顺序对算术运算符进行排序：

- 后缀增量 `x++` 和减量 `x--` 运算符。
- 前缀增量 `++x` 和减量 `--x` 以及一元 `+` 和 `-` 运算符。
- 乘法 `*`、`/` 和 `%` 运算符。
- 加法 `+` 和 `-` 运算符。

二元算数运算符是左结合运算符。 也就是说，具有相同优先级的运算符按从左至右的顺序计算。

使用括号 `()` 更改由运算符优先级和关联性决定的计算顺序。

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

要了解按优先级排序的完整 C# 运算符列表，请参阅 [C# 运算符](index.md)。

## <a name="compound-assignment"></a>复合赋值

对于二元运算符 `op`，窗体的复合赋值表达式

```csharp
x op= y
```

等效于

```csharp
x = x op y
```

不同的是 `x` 只计算一次。

以下示例使用算术运算符演示了复合赋值的用法：

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

还可以使用 `+=` 和 `-=` 运算符订阅和取消订阅[事件](../keywords/event.md)。 有关详细信息，请参阅[如何：订阅和取消订阅事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="arithmetic-overflow-and-division-by-zero"></a>算术溢出和被零除

当算术运算的结果超出所涉及数值类型的可能有限值范围时，算术运算符的行为取决于其操作数的类型。

### <a name="integer-arithmetic-overflow"></a>整数算术溢出

整数被零除总是引发 <xref:System.DivideByZeroException>。

在整数算术溢出的情况下，溢出检查上下文（可能[已检查或未检查](../keywords/checked-and-unchecked.md)）将控制引发的行为：

- 在已检查的上下文中，如果在常数表达式中发生溢出，则会发生编译时错误。 否则，当在运行时执行此运算时，则引发 <xref:System.OverflowException>。
- 在未检查的上下文中，会通过丢弃任何不适应目标类型的高序位来将结果截断。

在使用[已检查和未检查的](../keywords/checked-and-unchecked.md)语句时，可以使用 `checked` 和 `unchecked` 运算符来控制溢出检查上下文，在该上下文中将计算一个表达式：

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

默认情况下，算术运算发生在 *unchecked* 上下文中。

### <a name="floating-point-arithmetic-overflow"></a>浮点运算溢出

使用 `float` 和 `double` 类型的算术运算永远不会引发异常。 使用这些类型的算术运算的结果可能是表示无穷大和非数字的特殊值之一：

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

对于 `decimal` 类型的操作数，算术溢出始终会引发 <xref:System.OverflowException>，并且被零除始终会引发 <xref:System.DivideByZeroException>。

## <a name="round-off-errors"></a>舍入误差

由于实数和浮点运算的浮点表达形式的常规限制，在使用浮点类型的计算中可能会发生舍入误差。 也就是说，表达式得出的结果可能与预期的数学运算结果不同。 以下示例演示了几种此类情况：

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

有关详细信息，请参阅 [System.Double](/dotnet/api/system.double#remarks)、[System.Single](/dotnet/api/system.single#remarks) 或 [System.Decimal](/dotnet/api/system.decimal#remarks) 参考页面上的注解。

## <a name="operator-overloadability"></a>运算符可重载性

用户定义类型可以[重载](../keywords/operator.md)一元（`++`、`--`、`+` 和 `-`）和二元（`*`、`/`、`%``+` 和 `-`）算术运算符。 重载二元运算符时，对应的复合赋值运算符也会隐式重载。 用户定义类型不能显式重载复合赋值运算符。

## <a name="c-language-specification"></a>C# 语言规范

有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：

- [后缀增量和减量运算符](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [前缀增量和减量运算符](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [一元加运算符](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [一元减运算符](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [乘法运算符](~/_csharplang/spec/expressions.md#multiplication-operator)
- [除法运算符](~/_csharplang/spec/expressions.md#division-operator)
- [余数运算符](~/_csharplang/spec/expressions.md#remainder-operator)
- [加法运算符](~/_csharplang/spec/expressions.md#addition-operator)
- [减法运算符](~/_csharplang/spec/expressions.md#subtraction-operator)
- [复合赋值](~/_csharplang/spec/expressions.md#compound-assignment)
- [checked 和 unchecked 运算符](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 运算符](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [.NET 中的数字](../../../standard/numerics.md)
