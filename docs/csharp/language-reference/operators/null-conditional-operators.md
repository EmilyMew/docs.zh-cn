---
title: NULL 条件运算符 - C# 参考
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348838"
---
# <a name="-and--null-conditional-operators-c-reference"></a>?. 和 ?[] null 条件运算符（C# 参考）

执行成员访问 (`?.`) 或索引 (`?[]`) 操作之前，测试左侧操作数的值为 null，如果左侧操作数计算结果为 `null`，则返回 `null`。

这些运算符可帮助编写更少的代码来处理 null 检查，尤其是对于下降到数据结构。

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

NULL 条件运算符采用最小化求值策略。  如果条件成员访问和索引操作链中的某个操作返回 NULL，则该链其余部分的执行将停止。  在下面的示例中，如果 `A`、`B` 或 `C` 的计算结果为 NULL，就不会执行 `E`。

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

NULL 条件成员访问的另一个用途是使用非常少的代码以线程安全的方式调用委托。  旧方法需要如下所示的代码：

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

新的方法是要简单得多：

```csharp
PropertyChanged?.Invoke(…)
```

新方法是线程安全的，因为编译器生成的代码仅评估 `PropertyChanged` 一次，从而使结果保持在临时变量中。 你需要显式调用 `Invoke` 方法，因为不存在 NULL 条件委托调用语法 `PropertyChanged?(e)`。

## <a name="language-specifications"></a>语言规范

有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的 [null 条件运算符](~/_csharplang/spec/expressions.md#null-conditional-operator)。 该语言规范是 C# 语法和用法的权威资料。

## <a name="see-also"></a>请参阅

- [??（空合运算符）](null-coalescing-operator.md)
- [C# 参考](../index.md)
- [C# 编程指南](../../programming-guide/index.md)