---
title: 通过 CLI 开始使用 .NET Core
description: 一个分步教程，演示如何使用 .NET Core 命令行接口 (CLI) 开始在 Windows、Linux 或 macOS 上使用 .NET Core。
author: cartermp
ms.date: 09/10/2018
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 92ca5149ad5f0e4a50c809a316123fbf77d4152d
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545359"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>通过命令行开始在 Windows/Linux/macOS 上使用 .NET Core

本主题将演示如何使用 .NET Core CLI 工具开始在计算机上开发跨平台应用。

如果熟悉 .NET Core CLI 工具集，请阅读 [.NET Core SDK 概述](../tools/index.md)。

## <a name="prerequisites"></a>系统必备

- [.NET Core SDK 2.1](https://www.microsoft.com/net/download/core)。
- 按需选择的文本编辑器或代码编辑器。

## <a name="hello-console-app"></a>Hello，控制台应用！

若要[查看或下载示例代码](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)，可以访问 dotnet/samples GitHub 存储库。 有关下载说明，请参阅[示例和教程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

打开命令提示符，创建一个名为“Hello”的文件夹。 导航到创建的文件夹，键入下列内容：

```console
dotnet new console
dotnet run
```

让我们进行快速演练：

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) 会创建一个最新的 `Hello.csproj` 项目文件，其中包含生成控制台应用所必需的依赖项。  它还将创建 `Program.cs`，这是包含应用程序的入口点的基本文件。

   `Hello.csproj`：

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   项目文件指定还原依赖项和生成程序所需的一切。

   * `OutputType` 标记指定我们要生成的可执行文件，即控制台应用程序。
   * `TargetFramework` 标记指定要定位的 .NET 实现代码。 在高级方案中，可以指定多个目标框架，并在单个操作中生成所有目标框架。 在本教程中，我们将仅针对 .NET Core 2.1 进行生成。

   `Program.cs`：

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   该程序从 `using System` 开始，这意味着“将 `System` 命名空间中的所有内容都纳入此文件的作用域”。 `System` 命名空间包括基本结构，如 `string` 或数值类型。

   接着定义一个名为 `Hello` 的命名空间。 你可以将其更改为任何你喜欢的名称。 在该命名空间中定义了一个名为 `Program` 的类，其中 `Main` 方法将字符串数组作为其参数。 此数组包含在调用编译的程序时所传递的参数列表。 按照这样，不使用此数组：程序所进行的全部操作就是编写“Hello World!” “Hello World!”。 稍后将对使用此参数的代码进行更改。

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` 隐式调用 [`dotnet restore`](../tools/dotnet-restore.md)。 `dotnet restore` 调用到 [NuGet](https://www.nuget.org/)（.NET 包管理器）以还原依赖项树。 NuGet 分析 Hello.csproj 文件、下载文件中定义的依赖项（或从计算机缓存中获取）并编写 obj/project.assets.json 文件，在编译和运行示例时需要使用该文件。

   > [!IMPORTANT]
   > 如果你使用的是 .NET Core 1.x 版本的 SDK，在调用 `dotnet new` 后，必须自行调用 `dotnet restore`。

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) 调用 [`dotnet build`](../tools/dotnet-build.md) 来确保已生成要生成的目标，然后调用 `dotnet <assembly.dll>` 运行目标应用程序。

    ```console
    $ dotnet run
    Hello World!
    ```

    或者，还可以执行 [`dotnet build`](../tools/dotnet-build.md) 来编译代码，无需运行已生成的控制台应用程序。 这使得编译的应用程序（作为 DLL 文件）可以在 Windows 上使用 `dotnet bin\Debug\netcoreapp2.1\Hello.dll` 运行（将 `/` 用于非 Windows 系统）。 还可以对应用程序指定参数，相关操作将在本主题稍后部分进行介绍。

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    在高级方案中，可以将应用程序作为独立的特定于平台的文件集生成，该应用程序可以在未安装 .NET Core 的计算机上部署或运行。 请参阅 [.NET Core 应用程序部署](../deploying/index.md)了解详细信息。

### <a name="augmenting-the-program"></a>扩充程序

让我们稍微更改一下程序。 Fibonacci 数字很有意思，那么除了使用参数，让我们也来添加 Fibonacci 数字，让运行应用的用户开心一下。

1. 将 *Program.cs* 文件的内容替换为以下代码：

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. 执行 [`dotnet build`](../tools/dotnet-build.md) 以编译更改。

3. 运行向应用传递参数的程序：

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

就是这么简单！  可以按任意喜欢的方式扩充 `Program.cs`。

## <a name="working-with-multiple-files"></a>使用多个文件

单个文件适用于简单的一次性程序，但如果要构建较为复杂的应用，则项目中可能会有多个源文件。
我们通过缓存一些 Fibonacci 值并添加一些递归特性来基于之前的 Fibonacci 示例进行构建。

1. 使用以下代码将新文件添加到名为 *FibonacciGenerator.cs* 的 *Hello* 目录：

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. 更改 *Program.cs* 文件中的 `Main` 方法，以实例化新的类并调用其方法，如下例所示：

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. 执行 [`dotnet build`](../tools/dotnet-build.md) 以编译更改。

4. 通过执行 [`dotnet run`](../tools/dotnet-run.md) 来运行应用。 以下是程序输出：

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

就是这么简单！ 现在，可以开始使用此处学到的基本概念来创建自己的程序了。

请注意，本教程中用来运行应用程序的命令和步骤仅用于开发过程。 准备好部署应用后，需要查看适用于 .NET Core 应用的不同[部署策略](../deploying/index.md)和 [`dotnet publish`](../tools/dotnet-publish.md) 命令。

## <a name="see-also"></a>请参阅

- [使用 .NET Core CLI 工具组织和测试项目](testing-with-cli.md)
