---
title: 基于 Roslyn 的分析器 - .NET
description: 了解基于 Roslyn 的分析器，用其发现问题并针对这些问题提供修复建议。
author: billwagner
ms.author: wiwagn
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 436cfb3904f0891f8c18bb5890563a13d65e2d1c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634240"
---
# <a name="the-roslyn-based-analyzers"></a>基于 Roslyn 的分析器

基于 Roslyn 的分析器使用 .NET Compiler SDK (Roslyn Api) 来分析项目源代码，以找到问题并提供更正建议。 不同分析器寻找不同种类的问题，范围从有可能导致 bug 的做法到有关 API 兼容性的安全问题。

基于 Roslyn 的分析器以交互方式工作并在生成期间运行。 分析器将在 Visual Studio 或命令行生成过程中提供不同的指导。

当你在 Visual Studio 中编辑代码时，分析器会在你进行更改时运行，一旦创建触发问题的代码，它便会捕获可能存在的问题。 对于任何问题，均会在其下用波浪线进行突出显示。 Visual Studio 会显示一个灯泡，单击它时，分析器将针对该问题给出可能的修复建议。 生成项目时，将在 Visual Studio 中或通过命令行分析所有源代码，并且分析器会提供潜在问题的完整列表。 下图显示了一个示例。

![框架分析器报告的问题](./media/framework-analyzers-2.png)

基于 Roslyn 的分析器会报告潜在问题，如错误、警告或基于问题严重程度的信息。

在项目中，可以将基于 Roslyn 的分析器作为 NuGet 包进行安装。 已配置的分析器以及每个分析器的任何设置都将恢复，并在该项目任何开发人员的计算机上运行。

> [!NOTE]
> 基于 Roslyn 的分析器的用户体验与旧版本的 FxCop 和安全分析工具等代码分析库的用户体验不同。  你不必显式运行基于 Roslyn 的分析器。 无需在 Visual Studio 的“分析”菜单上使用“运行代码分析”菜单项。 基于 Roslyn 的分析器会在你工作时异步运行。

## <a name="more-information-on-specific-analyzers"></a>有关特定分析器的详细信息

本部分中将介绍以下分析器：

* [API 分析器](api-analyzer.md)：此分析器检查代码是否存在潜在的兼容性风险，或者是否使用了弃用的 API。
* [框架分析器](framework-analyzer.md)：此分析器对代码进行检查，确保它遵循 .NET Framework 应用程序的准则。 这些规则包括多个基于安全的建议。
* [.NET 可移植性分析器](portability-analyzer.md)：此分析器检查代码以了解让应用与其他 .NET 实现和配置文件（包括 .NET Core、.NET Standard、UWP 以及适用于 iOS、Android 和 Mac 的 Xamarin）兼容所需的工作量。
