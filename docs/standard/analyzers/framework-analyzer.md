---
title: .NET 安全分析器 - .NET
description: 了解如何使用 .NET Framework 分析器包中的.NET 安全分析器来查找和解决安全风险
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 562d85d47791ca253655dd05a1c9a268767ba949
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634461"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework 分析器

.NET Framework 分析器可用于查找基于 .NET Framework 的应用程序代码中存在的潜在问题。 此分析器会找到潜在问题并给出问题的修复建议。

分析器在编写代码时在 Visual Studio 中以交互方式运行，或作为 CI 生成的一部分。 在开发过程中，应尽早将分析器添加至项目。 越早找到代码中的潜在问题，这些问题就越早得到修复。 不过你可以将其添加至开发周期中的任何时间点。 它会找到现有代码中的问题，并在持续开发的过程中对新问题进行警告。

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>安装并配置 .NET Framework 分析器

.NET Framework 分析器必须以 NuGet 包的形式安装在每个需要它项目上。 只有一个开发人员需要将它们添加到项目。 分析器包是项目依赖项，并且一旦具有更新的解决方案就会在每个开发人员的计算机上运行。

[Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet 包中提供了 .NET Framework 分析器。 此包只提供特定于 .NET Framework 的分析器，其中包括安全分析器。 大多数情况下，你将需要 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 包。 FxCopAnalyzers 聚合包中包含了 Framework.Analyzers 包中的所有框架分析器以及下列分析器：
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers)：提供通用指南和.NET Standard API 指南
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers)：提供特定于 .NET Core API 的分析器。
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers)：提供作为代码包含的文本指南（包括注释）。

若要进行安装，请右键单击项目，并选择“管理依赖项”。
在 NuGet 资源管理器中搜索“NetFramework 分析器”，或根据自己的喜好选择“Fx Cop 分析器”。 将最新稳定版本安装至解决方案中的所有项目。

## <a name="using-the-net-framework-analyzer"></a>使用 .NET Framework 分析器

安装 NuGet 包后，生成解决方案。 分析器将报告它在基本代码中找到的所有问题。 问题将以警告形式在 Visual Studio 错误列表窗口中报告，如下图中所示：

![框架分析器报告的问题](./media/framework-analyzers-2.png)

编写代码时，代码中所有的潜在问题下方都会有波浪线。
将鼠标悬停在问题位置就能看到该问题的详细信息和可能的修复方法建议，如下图所示：

![框架分析器所发现问题的交互式报告](./media/framework-analyzers-1.png)

分析器会检查解决方案中的代码，并对下列所有问题提供警告列表：

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058:类型不应扩展某些基类型

.NET Framework 中有少量不应直接自其派生的类型。 

**类别：** 设计

**严重性：** 警告

其他信息：[CA:1058：类型不应扩展某些基类型](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153:请勿捕获损坏状态异常

捕获损坏状态异常可能会掩盖错误（例如，访问冲突），导致执行状态不一致或使系统更容易遭到攻击者的破坏。 改为捕获并处理更精确的异常类型或重新引发异常

**类别：** 安全性

**严重性：** 警告

其他信息：[## CA2153：请勿捕获损坏状态异常](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229:实现序列化构造函数

在创建实现 <xref:System.Runtime.Serialization.ISerializable> 接口的类型却没有定义所需序列化构造函数时，分析器会生成此警告。 要修复与该规则的冲突，请实现序列化构造函数。 对于密封类，请使构造函数成为私有；否则，请使构造函数成为受保护。 序列化构造函数具有以下签名：

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**类别：** 用法

**严重性：** 警告

其他信息：[CA2229：实现序列化构造函数](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235:标记所有不可序列化的字段

在可以序列化的类型中声明了类型不可序列化的实例字段。 必须用 <xref:System.NonSerializedAttribute> 对该字段进行显式标记以修复此警告。

**类别：** 用法

**严重性：** 警告

其他信息：[CA2235：标记所有不可序列化的字段](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237:用 serializable 标记 ISerializable 类型

若要被公共语言运行时识别为可序列化，类型必须用 <xref:System.SerializableAttribute> 特性标记，即使该类型通过实现 <xref:System.Runtime.Serialization.ISerializable> 接口使用自定义序列化例程也是如此。

**类别：** 用法

**严重性：** 警告

其他信息：[CA2237：用 serializable 标记 ISerializable 类型](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075:XML 中不安全的 DTD 处理

如果使用不安全的 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 实例或引用外部实体源，分析器可能会接受不受信任的输入并将敏感信息泄露给攻击者。  

**类别：** 安全性

**严重性：** 警告

其他信息：[A3075：XML 中不安全的 DTD 处理](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350:请勿使用弱加密算法

随着攻击越来越高级，加密算法会相对退化。 根据加密算法的类型和应用，其加密强度的进一步降低可能会使攻击者读取到加密消息、篡改加密消息、伪造数字签名、篡改经过哈希处理的内容或者破坏基于此算法的所有加密系统。 加密时，请使用 AES 算法（AES-256、AES-192 和 AES-128 都可以）并确保密钥长度大于或等于 128 位。 进行哈希处理时，请使用 SHA-2 系列中的哈希函数，例如 SHA-2 512、SHA-2 384 或 SHA-2 256。

**类别：** 安全性

**严重性：** 警告

其他信息：[CA5350：请勿使用弱加密算法](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351：请勿使用损坏的加密算法

在计算上，攻击可以破坏现有算法。 这使得攻击者可以破坏本应提供的加密保障。 根据加密算法的类型和应用，这可能会使攻击者读取到加密消息、篡改加密消息、伪造数字签名、篡改经过哈希处理的内容或者破坏基于此算法的所有加密系统。 加密时，请使用 AES 算法（AES-256、AES-192 和 AES-128 都可以）并确保密钥长度大于或等于 128 位。 进行哈希处理时，请使用 SHA-2 系列中的哈希函数，例如 SHA512、SHA384 或 SHA256。 进行数字签名时，请使用 RSA 并确保密钥长度大于或等于 2048 位，或使用 ECDSA 并确保密钥长度大于或等于 256 位。

**类别：** 安全性

**严重性：** 警告

其他信息：[CA5351:请勿使用损坏的加密算法](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)


