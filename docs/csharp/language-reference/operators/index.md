---
title: C# 运算符
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 7666918cbff7a395a93a274629fe574ff20e170c
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545684"
---
# <a name="c-operators"></a>C# 运算符

C# 提供了许多运算符，这些运算符是指定要在表达式中执行哪些操作（数学、索引、函数调用等等）的符号。 可以[重载](../../programming-guide/statements-expressions-operators/overloadable-operators.md)许多应用于用户定义类型的运算符，从而更改其含义。

对整数类型执行的运算（如 `==`、`!=`、`<`、`>`、`&`、`|`）通常也可对枚举 (`enum`) 类型执行。

以下章节按最高优先级到最低优先级的顺序列示 C# 运算符。 各章节内运算符的优先级相同。

## <a name="primary-operators"></a>主要运算符

以下是具有最高优先级的运算符。

[x.y](member-access-operator.md)：成员访问。

[x?.y](null-conditional-operators.md)：null 条件成员访问。 如果左操作数计算结果为 `null`，则返回 `null`。

[x?[y]](null-conditional-operators.md)：null 条件索引访问。 如果左操作数计算结果为 `null`，则返回 `null`。

[f(x)](invocation-operator.md)：函数调用。

[a&#91;x&#93;](index-operator.md)：聚合对象索引。

[x++](arithmetic-operators.md#increment-operator-)：后缀递增。 先返回 x 值，然后用加 1（通常加整数 1）后的 x 值更新存储位置。

[x--](arithmetic-operators.md#decrement-operator---)：后缀递减。 先返回 x 值，然后用减 1（通常减整数 1）后的 x 值更新存储位置。

[new](../keywords/new-operator.md)：类型实例化。

[typeof](../keywords/typeof.md) - 返回表示操作数的 <xref:System.Type> 对象。

[checked](../keywords/checked.md)：对整数运算启用溢出检查。

[unchecked](../keywords/unchecked.md)：对整数运算禁用溢出检查。 这是默认的编译器行为。

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 生成类型 T 的默认值。

[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md)：声明并返回委托实例。

[sizeof](../keywords/sizeof.md)：返回类型操作数的大小（以字节为单位）。

[->](dereference-operator.md)：指针取消引用与成员访问相结合。

## <a name="unary-operators"></a>一元运算符

这些运算符的优先级比下一章节高，比上一章节低。

[+x](addition-operator.md)：返回 x 的值。

[-x](subtraction-operator.md)：数值取反。

[\!x](logical-negation-operator.md)：逻辑取反。

[~x](bitwise-complement-operator.md)：按位求补。

[++x](arithmetic-operators.md#increment-operator-)：前缀递增。 先用加 1（通常加整数 1）后的 x 值更新存储位置，然后返回 x 值。

[--x](arithmetic-operators.md#decrement-operator---)：前缀递减。 先用减 1（通常减整数 1）后的 x 值更新存储位置，然后返回 x 值。

[(T)x](invocation-operator.md)：类型显式转换。

[await](../keywords/await.md)：等待 `Task`。

[&x](and-operator.md)：地址。

[*x](multiplication-operator.md)：取消引用。

## <a name="multiplicative-operators"></a>乘法运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x * y](arithmetic-operators.md#multiplication-operator-)：乘法。

[x / y](arithmetic-operators.md#division-operator-)：除法。 如果操作数均为整数，则结果为整数，舍去小数（例如，`-7 / 2 is -3`）。

[x % y](arithmetic-operators.md#remainder-operator-)：余数。 如果操作数均为整数，则返回 x 除以 y 后的余数。  如果 `q = x / y` 且 `r = x % y`，则 `x = q * y + r`。

## <a name="additive-operators"></a>相加运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x + y](arithmetic-operators.md#addition-operator-)：加法。

[x - y](arithmetic-operators.md#subtraction-operator--)：减法。

## <a name="shift-operators"></a>移位运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x <\<  y](left-shift-operator.md)：左移位，右侧用 0 填充。

[x >> y](right-shift-operator.md)：右移位。 如果左操作数是 `int` 或 `long`，则左位数补符号位。 如果左操作数是 `uint` 或 `ulong`，则左位数补零。

## <a name="relational-and-type-testing-operators"></a>关系和类型测试运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x \< y](less-than-operator.md)：小于（如果 x 小于 y，则为 true）。

[x > y](greater-than-operator.md)：大于（如果 x 大于 y，则为 true）。

[x \<= y](less-than-equal-operator.md)：小于或等于。

[x >= y](greater-than-equal-operator.md)：大于或等于。

[is](../keywords/is.md)：类型兼容性。 如果求值后的左操作数可以转换为右操作数中指定的类型（静态类型），则返回 true。

[as](../keywords/as.md)：类型转换。 返回左操作数并转换为右操作数中指定的类型（静态类型），但 `as` 返回 `null`，其中 `(T)x` 会引发异常。

## <a name="equality-operators"></a>相等运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x == y](equality-operators.md#equality-operator-)：相等。 默认情况下，对于 `string` 以外的引用类型，此运算符返回引用相等（标识测试）。 但是，类型可以重载 `==`，因此，如果你想测试标识，最好对 `object` 使用 `ReferenceEquals` 方法。

[x != y](equality-operators.md#inequality-operator-)：不相等。 请参阅有关 `==` 的注释。 如果某个类型重载 `==`，则它必须重载 `!=`。

## <a name="logical-and-operator"></a>逻辑 AND 运算符

此运算符的优先级比下一章节高，比上一章节低。

[x & y](and-operator.md)：逻辑或位 AND。 通常可以将此运算符与整数类型和 `enum` 类型一起使用。

## <a name="logical-xor-operator"></a>辑 XOR 运算

此运算符的优先级比下一章节高，比上一章节低。

[x ^ y](xor-operator.md)：逻辑或位 XOR。 通常可以将此运算符与整数类型和 `enum` 类型一起使用。

## <a name="logical-or-operator"></a>逻辑 OR 运算符

此运算符的优先级比下一章节高，比上一章节低。

[x &#124; y](or-operator.md)：逻辑或位 OR。 通常可以将此运算符与整数类型和 `enum` 类型一起使用。

## <a name="conditional-and-operator"></a>条件 AND 运算符

此运算符的优先级比下一章节高，比上一章节低。

[x && y](conditional-and-operator.md)：逻辑 AND。 如果第一个操作数计算结果为 false，则 C# 不对第二个操作数求值。

## <a name="conditional-or-operator"></a>条件 OR 运算符

此运算符的优先级比下一章节高，比上一章节低。

[x &#124;&#124; y](conditional-or-operator.md)：逻辑 OR。 如果第一个操作数计算结果为 true，则 C# 不对第二个操作数求值。

## <a name="null-coalescing-operator"></a>Null 合并运算符

此运算符的优先级比下一章节高，比上一章节低。

[x ?? y](null-coalescing-operator.md)：如果不为 `null`，则返回 `x`；否则返回 `y`。

## <a name="conditional-operator"></a>条件运算符

此运算符的优先级比下一章节高，比上一章节低。

[t ? x : y](conditional-operator.md) - 如果测试 `t` 计算结果为 true，则计算并返回 `x`；否则，计算并返回 `y`。

## <a name="assignment-and-lambda-operators"></a>赋值和 Lambda 运算符

这些运算符的优先级比下一章节高，比上一章节低。

[x = y](assignment-operator.md)：赋值。

[x += y](addition-assignment-operator.md)：递增。 `x` 值加 `y` 值，结果存储在 `x` 中，并返回新值。 如果 `x` 指定 `event`，则 `y` 必须是 C# 作为事件处理程序添加的相应函数。

[x -= y](subtraction-assignment-operator.md)：递减。 `x` 值减 `y` 值，结果存储在 `x` 中，并返回新值。 如果 `x` 指定 `event`，则 `y` 必须是 C# 作为事件处理程序删除的相应函数

[x *= y](multiplication-assignment-operator.md)：乘法赋值。 `x` 值乘以 `y` 值，结果存储在 `x` 中，并返回新值。

[x /= y](arithmetic-operators.md#compound-assignment)：除法赋值。 `x` 值除以 `y` 值，结果存储在 `x` 中，并返回新值。

[x %= y](arithmetic-operators.md#compound-assignment)：余数赋值。 `x` 值除以 `y` 值，余数存储在 `x` 中，并返回新值。

[x &= y](and-assignment-operator.md)：AND 赋值。 `y` 值和 `x` 值相与，结果存储在 `x` 中，并返回新值。

[x &#124;= y](or-assignment-operator.md)：OR 赋值。 `y` 值和 `x` 值相或，结果存储在 `x` 中，并返回新值。

[x ^= y](xor-assignment-operator.md)：XOR 赋值。 `y` 值和 `x` 值相异或，结果存储在 `x` 中，并返回新值。

[x <<= y](left-shift-assignment-operator.md)：左移赋值。 将 `x` 值向左移动 `y` 位，结果存储在 `x` 中，并返回新值。

[x >>= y](right-shift-assignment-operator.md)：右移赋值。 将 `x` 值向右移动 `y` 位，结果存储在 `x` 中，并返回新值。

[=>](lambda-operator.md)：lambda 声明。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C#](../../index.md)
- [可重载运算符](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [C# 关键字](../keywords/index.md)