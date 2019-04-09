---
title: .NET Core 和 .NET Standard 中的单元测试
description: 本文简要概述了 .NET Core 和.NET Standard 项目的单元测试。
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 73667843452bbcab52a8cd4aa7906beecc095677
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185501"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core 和 .NET Standard 中的单元测试

通过 .NET Core，可以轻松创建单元测试。 本文介绍了单元测试及其与其他类型的测试的不同之处。 页面底部附近的链接资源介绍了如何向解决方案添加测试项目。 设置测试项目后，可使用命令行或 Visual Studio 运行单元测试。

.NET Core 2.0 及更高版本支持 [.NET Standard 2.0](../../standard/net-standard.md)，我们将使用它的库来演示单元测试。

可以使用适用于 C#、F# 和 Visual Basic 的内置 .NET Core 2.0 及更高版本单元测试项目模板作为个人项目的起始点。

## <a name="what-are-unit-tests"></a>什么是单元测试？

使用自动测试是确保软件应用程序按作者期望执行操作的一种绝佳方式。 软件应用程序有多种类型的测试。 其中包括集成测试、Web 测试、负载测试和其他测试。 “单元测试”用于测试个人软件组件或方法。 单元测试仅应测试开发人员控件内的代码。 它们不应测试基础结构问题。 基础结构问题包括数据库、文件系统和网络资源。 

此外，请记住还可使用编写测试的最佳做法。 例如，[测试驱动开发 (TDD)](https://deviq.com/test-driven-development/) 是指先编写单元测试，再编写该单元测试要检查的代码。 TDD 就像先编写书籍大纲，再编写该书籍。 它旨在帮助开发人员编写更简单、更具可读性的高效代码。 

> [!NOTE]
> ASP.NET 团队遵循[这些约定](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)帮助开发人员为测试类和方法提供合适的名称。

编写单元测试时，尽量不要引入基础结构依赖项。 这些依赖项会降低测试速度，使测试更加脆弱，应将其保留供集成测试使用。 可以通过遵循 [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/)（显式依赖项原则）和使用 [Dependency Injection](/aspnet/core/fundamentals/dependency-injection)（依赖项注入）避免应用程序中的这些依赖项。 还可以将单元测试保留在单独的项目中，与集成测试相分隔。 这可确保单元测试项目没有引用或依赖于基础结构包。

## <a name="next-steps"></a>后续步骤

有关 .NET Core 项目中的单元测试的详细信息：

.NET Core 单元测试项目支持：
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

还可以在以下各项之间进行选择：
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/testfx-docs)

可在以下演练中了解详细信息：

* [结合使用 .NET Core CLI 与 xUnit 和 C#](unit-testing-with-dotnet-test.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 NUnit 和 C#](unit-testing-with-nunit.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 MSTest 和 C#](unit-testing-with-mstest.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 xUnit 和 F#](unit-testing-fsharp-with-dotnet-test.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 NUnit 和 F#](unit-testing-fsharp-with-nunit.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 MSTest 和 F#](unit-testing-fsharp-with-mstest.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 xUnit 和 Visual Basic](unit-testing-visual-basic-with-dotnet-test.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 NUnit 和 Visual Basic](unit-testing-visual-basic-with-nunit.md) 创建单元测试。
* [结合使用 .NET Core CLI 与 MSTest 和 Visual Basic](unit-testing-visual-basic-with-mstest.md) 创建单元测试。

可在以下文章中了解详细信息：

* Visual Studio Enterprise 提供用于 .NET Core 的卓越测试工具。 有关详细信息，请查看 [Live Unit Testing](/visualstudio/test/live-unit-testing) 或[代码覆盖率](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)。
* 有关如何运行选择性单元测试的详细信息，请参阅[运行选择性单元测试](selective-unit-tests.md)或[使用 Visual Studio 添加和排除测试](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。
* [如何通过 .NET Core 和 Visual Studio 使用 xUnit](https://xunit.github.io/docs/getting-started-dotnet-core.html)。
