---
title: + 运算符 - C# 参考
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504465"
---
# <a name="-operator-c-reference"></a>+ 运算符（C# 参考）

以下两种形式支持 `+` 运算符：一元加运算符或二元加运算符。

## <a name="unary-plus-operator"></a>一元加运算符

一元 `+` 运算符返回其操作数的值。 它受所有数值类型支持。

## <a name="numeric-addition"></a>数值加

对于数字类型，`+` 运算符计算其操作数的和：

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

有关算术运算符的详细信息，请参阅[算术运算符](arithmetic-operators.md)。

## <a name="string-concatenation"></a>字符串串联

当其中的一个操作数是[字符串](../keywords/string.md)类型或两个操作数都是字符串类型时，`+` 运算符将其操作数的字符串表示形式串联在一起：

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

从 C# 6 开始，[字符串内插](../tokens/interpolated.md)提供了格式化字符串的更便捷方式：

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>委托组合

对于[委托](../keywords/delegate.md)类型，`+` 运算符在调用时返回新的委托实例，调用第一个操作数，然后调用第二个操作数。 如果任何操作数均为 `null`，则 `+` 运算符将返回另一个操作数（也可能是 `null`）的值。 下面的示例演示如何组合使用委托和 `+` 运算符：

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

有关委托类型的详细信息，请参阅[委托](../../programming-guide/delegates/index.md)。

## <a name="operator-overloadability"></a>运算符可重载性

用户定义的类型可以[重载](../keywords/operator.md)一元和二元 `+` 运算符。 重载二元 `+` 运算符后，也会隐式重载[加法赋值运算符](addition-assignment-operator.md) `+=`。

## <a name="c-language-specification"></a>C# 语言规范

有关详细信息，请参阅[C# 语言规范](../language-specification/index.md)的[一元加运算符](~/_csharplang/spec/expressions.md#unary-plus-operator)和[加法运算符](~/_csharplang/spec/expressions.md#addition-operator)部分。

## <a name="see-also"></a>请参阅

- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)
- [C# 运算符](index.md)
- [字符串内插](../tokens/interpolated.md)
- [如何：连接多个字符串](../../how-to/concatenate-multiple-strings.md)
- [委托](../../programming-guide/delegates/index.md)
- [Checked 和 unchecked](../keywords/checked-and-unchecked.md)
