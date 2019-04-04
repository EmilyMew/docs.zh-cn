---
title: 相等运算符 - C# 参考
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545886"
---
# <a name="equality-operators-c-reference"></a>相等运算符（C# 参考）

[`==`（相等）](#equality-operator-) 和 [`!=`（不等）](#inequality-operator-) 运算符检查其操作数是否相等。

## <a name="equality-operator-"></a>相等运算符 ==

如果操作数相等，等于运算符 `==` 返回 `true`，否则返回 `false`。

### <a name="value-types-equality"></a>值类型的相等性

如果[内置值类型](../keywords/value-types-table.md)的值相等，则其操作数相等：

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> 对于相等和关系运算符 `==`、`>`、`<`、`>=` 和 `<=`，如果任何操作数不是数字（<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>），则操作数的结果为 `false`。 这意味着 `NaN` 值不大于、小于或等于任何其他 `double`（或 `float`）值，包括 `NaN`。 有关更多信息和示例，请参阅 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 参考文章。

如果基本整数类型的相应值相等，则相同[枚举](../keywords/enum.md)类型的两个操作数相等。

用户定义的 [struct](../keywords/struct.md) 类型默认情况下不支持 `==` 运算符。 要支持 `==` 运算符，用户定义的结构必须[重载](#operator-overloadability)它。

从 C# 7.3 开始，`==` 和 `!=` 运算符由 C# [元组](../../tuples.md)支持。 有关详细信息，请参阅 [C# 元组类型](../../tuples.md)一文的[相等性和元组](../../tuples.md#equality-and-tuples)部分。

### <a name="string-equality"></a>字符串相等性

如果两个字符串均为 `null` 或者两个字符串实例具有相等长度且在每个字符位置有相同字符，则这两个[字符串](../keywords/string.md)操作数相等：

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

这就是区分大小写的序号比较。 有关字符串比较的详细信息，请参阅[如何在 C# 中比较字符串](../../how-to/compare-strings.md)。

### <a name="reference-types-equality"></a>引用类型的相等性

当两个非 `string` 引用类型引用同一对象时，其操作数相等：

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

如示例所示，默认情况下，用户定义的引用类型支持 `==` 运算符。 但是，用户定义的引用类型可以重载 `==` 运算符。 如果引用类型重载 `==` 运算符，使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法来检查该类型的两个引用是否引用同一对象。

## <a name="inequality-operator-"></a>不等运算符 !=

如果操作数不相等，不等于运算符 `!=` 返回 `true`，否则返回 `false`。 对于[内置类型](../keywords/built-in-types-table.md)的操作数，表达式 `x != y` 生成与表达式 `!(x == y)` 相同的结果。 有关类型相等性的更多信息，请参阅[相等运算符](#equality-operator-)部分。

下面的示例演示 `!=` 运算符的用法：

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>运算符可重载性

用户定义的类型可以[重载](../keywords/operator.md) `==` 和 `!=` 运算符。 如果某类型重载这两个运算符之一，它还必须重载另一个运算符。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[关系和类型测试运算符](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)部分。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 运算符](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [相等性比较](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
