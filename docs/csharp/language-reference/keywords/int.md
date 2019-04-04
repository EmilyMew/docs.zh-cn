---
title: int - C# 参考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 6cabc2c6d4930c5d5fc88e76a17c1a6425ddd1bd
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185774"
---
# <a name="int-c-reference"></a>int（C# 参考）

`int` 表示一种整型类型，该类型根据下表显示的大小和范围存储值。

|类型|范围|大小|.NET 类型|
|----------|-----------|----------|-------------------------|
|`int`|-2,147,483,648 到 2,147,483,647|带符号的 32 位整数|<xref:System.Int32?displayProperty=nameWithType>|

## <a name="literals"></a>文本

可以通过为其分配十进制文本、十六进制文本或（从 C# 7.0 开始）二进制文本来声明和初始化 `int` 变量。  如果整数文本在 `int` 范围之外（即，如果它小于 <xref:System.Int32.MinValue?displayProperty=nameWithType> 或大于 <xref:System.Int32.MaxValue?displayProperty=nameWithType>），会发生编译错误。

在以下示例中，表示为十进制、十六进制和二进制文本且等于 90,946 的整数被分配给 `int` 值。

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]

> [!NOTE]
> 使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。 十进制文本没有前缀。

从 C# 7.0 开始，添加了一些功能以增强可读性。
- C# 7.0 允许将下划线字符 (`_`) 用作数字分隔符。
- C# 7.2 允许将 `_` 用作二进制或十六进制文本的数字分隔符，位于前缀之后。 十进制文本不能够有前导下划线。

下面是一些示例。

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]

整数文本还可以包括一个表示类型的后缀，尽管没有表示 `int` 类型的后缀。 如果整数文本没有后缀，则其类型为以下类型中可表示其值的第一个类型：

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md)

在这些示例中，文本 90946 属于类型 `int`。

## <a name="conversions"></a>转换

存在从 `int` 到 [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的预定义隐式转换。 例如:

```csharp
// '123' is an int, so an implicit conversion takes place here:
float f = 123;
```

存在从 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 到 `int` 的预定义隐式转换。 例如，如果不使用转换，以下赋值语句会生成编译错误：

```csharp
long aLong = 22;
int i1 = aLong;       // Error: no implicit conversion from long.
int i2 = (int)aLong;  // OK: explicit conversion.
```

另请注意，不存在从浮点类型到 `int` 类型的隐式转换。 例如，除非使用显式强制转换，否则以下语句将生成编译器错误：

```csharp
int x = 3.0;         // Error: no implicit conversion from double.
int y = (int)3.0;    // OK: explicit conversion.
```

有关兼用浮点类型和整型类型的算术表达式的详细信息，请参阅 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的[整型类型](~/_csharplang/spec/types.md#integral-types)。 该语言规范是 C# 语法和用法的权威资料。

## <a name="see-also"></a>请参阅

- <xref:System.Int32>
- [C# 参考](../../../csharp/language-reference/index.md)
- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [C# 关键字](../../../csharp/language-reference/keywords/index.md)
- [整型表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [内置类型表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [显式数值转换表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
