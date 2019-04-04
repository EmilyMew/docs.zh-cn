---
title: byte - C# 参考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 94ecc19294d82038e5406a05f8e1281d47e43081
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185904"
---
# <a name="byte-c-reference"></a>byte（C# 参考）

`byte` 表示存储下表所示值的整型类型。

|类型|范围|大小|.NET 类型|
|----------|-----------|----------|-------------------------|
|`byte`|0 到 255|无符号的 8 位整数|<xref:System.Byte?displayProperty=nameWithType>|

## <a name="literals"></a>文本

可以通过为其分配十进制文本、十六进制文本或（从 C# 7.0 开始）二进制文本来声明和初始化 `byte` 变量。 如果整数文本在 `byte` 范围之外（即，如果它小于 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大于 <xref:System.Byte.MaxValue?displayProperty=nameWithType>），会发生编译错误。

在以下示例中，等于 201、表示为十进制、十六进制和二进制文本的整数从 [int](../../../csharp/language-reference/keywords/int.md) 隐式转换为 `byte` 值。

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]

> [!NOTE]
> 使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。 十进制文本没有前缀。

从 C# 7.0 开始，添加了一些功能以增强可读性。
- C# 7.0 允许将下划线字符 (`_`) 用作数字分隔符。
- C# 7.2 允许将 `_` 用作二进制或十六进制文本的数字分隔符，位于前缀之后。 十进制文本不能够有前导下划线。

下面是一些示例。

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]

## <a name="conversions"></a>转换

存在从 `byte` 到 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的预定义隐式转换。

不可将大存储大小的非文本数字类型隐式转换为 `byte`。 有关整型类型存储大小的详细信息，请参阅[整型类型表](../../../csharp/language-reference/keywords/integral-types-table.md)。 以下面两个 `byte` 变量 `x` 和 `y` 为例：

```csharp
byte x = 10, y = 20;
```

以下赋值语句将产生一个编译器错误，原因是赋值运算符右侧的算术表达式在默认情况下的计算结果为 `int` 类型。

```csharp
// Error: conversion from int to byte:
byte z = x + y;
```

若要解决此问题，请使用强制转换：

```csharp
// OK: explicit conversion:
byte z = (byte)(x + y);
```

但是，在目标变量具有相同或更大的存储大小时，也可以使用下列语句：

```csharp
int x = 10, y = 20;
int m = x + y;
long n = x + y;
```

此外，不存在从浮点类型到 `byte` 类型的隐式转换。 例如，除非使用显式强制转换，否则以下语句将生成编译器错误：

```csharp
// Error: no implicit conversion from double:
byte x = 3.0;
// OK: explicit conversion:
byte y = (byte)3.0;
```

在调用重载方法时，必须使用转换。 以下面使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 参数的重载方法为例：

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(byte b) {}
```

使用 `byte` 强制转换可保证调用正确的类型，例如：

```csharp
// Calling the method with the int parameter:
SampleMethod(5);
// Calling the method with the byte parameter:
SampleMethod((byte)5);
```

有关兼用浮点类型和整型类型的算术表达式的信息，请参阅 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。

有关隐式数值转换规则的详细信息，请参阅[隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的[整型类型](~/_csharplang/spec/types.md#integral-types)。 该语言规范是 C# 语法和用法的权威资料。

## <a name="see-also"></a>请参阅

- <xref:System.Byte>
- [C# 参考](../../../csharp/language-reference/index.md)
- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [C# 关键字](../../../csharp/language-reference/keywords/index.md)
- [整型表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [内置类型表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [显式数值转换表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
