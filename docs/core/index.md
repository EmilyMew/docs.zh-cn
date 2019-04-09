---
title: .NET Core 指南
description: .NET Core 是一种用于创建 Windows、Linux 和 Mac 应用的模块式高性能的 .NET 实现。 了解 .NET Core 以开始使用。
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920618"
---
# <a name="net-core-guide"></a>.NET Core 指南

[.NET Core](about.md) 是[开放源代码](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)通用开发平台，由 Microsoft 和 .NET 社区在 [GitHub](https://github.com/dotnet/core) 上共同维护。 它跨平台（支持 Windows、macOS 和 Linux），并且可用于生成设备、云和 IoT 应用程序。

请参阅[关于 .NET Core](about.md)，以详细了解 .NET Core，包括它的特征、支持的语言和框架以及密钥 API。

请学习 [.NET Core 教程](tutorials/index.md)，了解如何创建简单的 .NET Core 应用程序。 只需几分钟即可生成并运行第一个应用。 若要尝试在浏览器中使用 .NET Core，请参阅 [C# 中的数字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)在线教程。

## <a name="download-net-core-22"></a>下载 .NET Core 2.2

下载 [.NET Core 2.2 SDK](https://www.microsoft.com/net/download)，以尝试在 Windows、macOS 或 Linux 计算机上使用 .NET Core。 若要使用 Docker 容器，请访问 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/)。

若要使用其他版本 .NET Core，可以在 [.NET Core 下载内容](https://www.microsoft.com/net/download/archives)中找到所有版本 .NET Core。

## <a name="net-core-22"></a>.NET Core 2.2

最新版是 [.NET Core 2.2](whats-new/dotnet-core-2-2.md)。 新功能包括：框架依赖部署、启动挂钩、使用 Azure SQL 进行 AAD 身份验证以及对 Windows ARM32 的支持。

## <a name="create-your-first-application"></a>创建首个应用程序

安装 .NET Core SDK 后，打开命令提示符。 键入以下 `dotnet` 命令以创建并运行 C# 应用程序。

```console
dotnet new console
dotnet run
```

您应看到以下输出：

```console
Hello World!
```

## <a name="support"></a>支持

[Microsoft 支持](https://www.microsoft.com/net/support/policy)在 Windows、macOS 和 Linux 上使用 .NET Core。 它每年会进行多次安全和质量更新（通常每月一次）。

.NET Core 二进制发行版是在 Azure 中的 Microsoft 维护服务器上进行生成和测试，并像其他任何 Microsoft 产品一样获得支持。

[Red Hat 支持在 Red Hat Enterprise Linux (RHEL) 上使用 .NET Core](http://redhatloves.net/)。 Red Hat 从源中生成 .NET Core，并在 [Red Hat 软件集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供它。 Red Hat 和 Microsoft 开展协作，共同确保 .NET Core 能够在 RHEL 上正常运行。
