---
title: 可重载运算符 - C# 编程指南
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: b4e4c3c6f73a10008093d727929f74e77c063239
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545489"
---
# <a name="overloadable-operators-c-programming-guide"></a>可重载运算符（C# 编程指南）

C# 通过使用 [operator](../../language-reference/keywords/operator.md) 关键字定义静态成员函数，来允许用户定义的类型重载运算符。 不过并非所有运算符都可以进行重载，并且其他运算符具有限制，如下表所列：

| 运算符 | 可重载性 |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md)、[-](../../language-reference/operators/subtraction-operator.md)、[!](../../language-reference/operators/logical-negation-operator.md)、[~](../../language-reference/operators/bitwise-complement-operator.md)、[++](../../language-reference/operators/arithmetic-operators.md#increment-operator-)、[--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---)、[true](../../language-reference/keywords/true-false-operators.md)、[false](../../language-reference/keywords/true-false-operators.md)|这些一元运算符可以进行重载。|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/and-operator.md), [&#124;](../../language-reference/operators/or-operator.md), [^](../../language-reference/operators/xor-operator.md), [\<\<](../../language-reference/operators/left-shift-operator.md), [>>](../../language-reference/operators/right-shift-operator.md)|这些二元运算符可以进行重载。|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|比较运算符可以进行重载（但是请参阅此表后面的备注）。|
|[&&](../../language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../language-reference/operators/conditional-or-operator.md)|条件逻辑运算符无法进行重载，但是它们使用 `&` 和 <code>&#124;</code>（可以进行重载）来计算。|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|数组索引运算符无法进行重载，但是可以定义[索引器](../indexers/index.md)。|
|[(T)x](../../language-reference/operators/invocation-operator.md)|强制转换运算符无法进行重载，但是可以定义新转换运算符（请参阅 [explicit](../../language-reference/keywords/explicit.md) 和 [implicit](../../language-reference/keywords/implicit.md)）。|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/and-assignment-operator.md), [&#124;=](../../language-reference/operators/or-assignment-operator.md), [^=](../../language-reference/operators/xor-assignment-operator.md), [\<\<=](../../language-reference/operators/left-shift-assignment-operator.md), [>>=](../../language-reference/operators/right-shift-assignment-operator.md)|赋值运算符不能显式重载。 但在重载二元运算符时，也会隐式重载相应的赋值运算符（若有）。 例如，使用 `+`（可以进行重载）计算 `+=`。|
|[=](../../language-reference/operators/assignment-operator.md)、[.](../../language-reference/operators/member-access-operator.md)、[?:](../../language-reference/operators/conditional-operator.md)、[??](../../language-reference/operators/null-coalescing-operator.md)、[->](../../language-reference/operators/dereference-operator.md)、[=>](../../language-reference/operators/lambda-operator.md)、[f(x)](../../language-reference/operators/invocation-operator.md)、[as](../../language-reference/keywords/as.md)、[checked](../../language-reference/keywords/checked.md)、[unchecked](../../language-reference/keywords/unchecked.md)、[default](../../programming-guide/statements-expressions-operators/default-value-expressions.md)、[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md)、[is](../../language-reference/keywords/is.md)、[new](../../language-reference/keywords/new.md)、[sizeof](../../language-reference/keywords/sizeof.md)、[typeof](../../language-reference/keywords/typeof.md)|这些运算符无法进行重载。|

> [!NOTE]
> 如果进行重载，则比较运算符必须成对进行重载；也就是说，如果 `==` 进行重载，则 `!=` 也必须进行重载。 反过来也成立，其中重载 `!=` 需要重载 `==`。 对于比较运算符 `<` 和 `>`，以及 `<=` 和 `>=`，也成立。

有关如何重载运算符的信息，请参阅[运算符](../../language-reference/keywords/operator.md)关键字文章。

## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [语句、表达式和运算符](index.md)
- [运算符](operators.md)
- [C# 运算符](../../language-reference/operators/index.md)
- [重载运算符为何在 C# 中始终是静态的？](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
