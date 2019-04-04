---
title: dotnet 命令
description: 了解 dotnet 命令（.NET Core CLI 工具的通用驱动程序）及其用法。
ms.date: 06/04/2018
ms.openlocfilehash: 107a529952cce62dac840874fa5d6d8986376adf
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185631"
---
# <a name="dotnet-command"></a>dotnet 命令

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet` - 一款管理 .NET 源代码和二进制文件的工具。

## <a name="synopsis"></a>摘要

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>说明

`dotnet` 是一款管理 .NET 源代码和二进制文件的工具。 它公开执行特定任务的命令，例如 [`dotnet build`](dotnet-build.md) 和 [`dotnet run`](dotnet-run.md)。 每个命令都定义自己的参数。 在每个命令后键入 `--help` 以访问简要帮助文档。

可以使用 `dotnet` 来运行应用程序，方法是指定应用程序 DLL，如 `dotnet myapp.dll`. 要了解部署选项，请参阅 [.NET Core 应用程序部署](../deploying/index.md)。

## <a name="options"></a>选项

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

其他 deps.json 文件的路径。

`--additionalprobingpath <PATH>`

包含要进行探测的探测策略和程序集的路径。

`-d|--diagnostics`

启用诊断输出。

`--fx-version <VERSION>`

用于运行应用程序的 .NET Core 运行时版本。

`-h|--help`

打印出给定命令的文档，如 `dotnet build --help`。 `dotnet --help` 打印可用命令列表。

`--info`

打印出有关 .NET Core 安装和计算机环境（如当前操作系统）的详细信息，并提交 .NET Core 版本的 SHA。

`--list-runtimes`

显示已安装的 .NET Core 运行时。

`--list-sdks`

显示已安装的 .NET Core SDK。

`--roll-forward-on-no-candidate-fx <N>`

所需的共享框架不可用时，请定义行为。 `N` 可以是：
* `0` - 禁用次要版本前滚。
* `1` - 前滚次要版本，但不前滚主版本。 这是默认行为。
* `2` - 前滚次要和主版本。

 有关详细信息，请参阅[前滚](../whats-new/dotnet-core-2-1.md#roll-forward)。

`-v|--verbosity <LEVEL>`

设置命令的详细级别。 允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 并非在每个命令中均受支持；请参阅特定的命令页，确定此选项是否可用。

`--version`

打印使用中的 .NET Core SDK 版本。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

其他 deps.json 文件的路径。

`--additionalprobingpath <PATH>`

包含要进行探测的探测策略和程序集的路径。

`-d|--diagnostics`

启用诊断输出。

`--fx-version <VERSION>`

用于运行应用程序的 .NET Core 运行时版本。

`-h|--help`

打印出给定命令的文档，如 `dotnet build --help`。 `dotnet --help` 打印可用命令列表。

`--info`

打印出有关 .NET Core 安装和计算机环境（如当前操作系统）的详细信息，并提交 .NET Core 版本的 SHA。

`--roll-forward-on-no-candidate-fx`

 如果设置为 `0`，则禁用次要版本前滚。 有关详细信息，请参阅[前滚](../whats-new/dotnet-core-2-1.md#roll-forward)。

`-v|--verbosity <LEVEL>`

设置命令的详细级别。 允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 并非在每个命令中均受支持；请参阅特定的命令页，确定此选项是否可用。

`--version`

打印使用中的 .NET Core SDK 版本。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

包含要进行探测的探测策略和程序集的路径。

`-d|--diagnostics`

启用诊断输出。

`--fx-version <VERSION>`

用于运行应用程序的 .NET Core 运行时版本。

`-h|--help`

打印出给定命令的文档，如 `dotnet build --help`。 `dotnet --help` 打印可用命令列表。

`--info`

打印出有关 .NET Core 安装和计算机环境（如当前操作系统）的详细信息，并提交 .NET Core 版本的 SHA。

`-v|--verbosity <LEVEL>`

设置命令的详细级别。 允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 并非在每个命令中均受支持；请参阅特定的命令页，确定此选项是否可用。

`--version`

打印使用中的 .NET Core SDK 版本。

---

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>常规

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| 命令                                       | 函数                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | 生成 .NET Core 应用程序。                                     |
| [dotnet build-server](dotnet-build-server.md) | 与通过生成启动的服务器进行交互。                          |
| [dotnet clean](dotnet-clean.md)               | 清除生成输出。                                                |
| [dotnet help](dotnet-help.md)                 | 显示命令更详细的在线文档。           |
| [dotnet migrate](dotnet-migrate.md)           | 将有效的预览版 2 项目迁移到 .NET Core SDK 1.0 项目。  |
| [dotnet msbuild](dotnet-msbuild.md)           | 提供对 MSBuild 命令行的访问权限。                        |
| [dotnet new](dotnet-new.md)                   | 为给定的模板初始化 C# 或 F# 项目。                |
| [dotnet pack](dotnet-pack.md)                 | 创建代码的 NuGet 包。                               |
| [dotnet publish](dotnet-publish.md)           | 发布 .NET 依赖于框架或独立应用程序。 |
| [dotnet restore](dotnet-restore.md)           | 还原给定应用程序的依赖项。                  |
| [dotnet run](dotnet-run.md)                   | 从源运行应用程序。                                   |
| [dotnet sln](dotnet-sln.md)                   | 用于添加、删除和列出解决方案文件中项目的选项。       |
| [dotnet store](dotnet-store.md)               | 将程序集存储到运行时包存储区。                     |
| [dotnet test](dotnet-test.md)                 | 使用测试运行程序运行测试。                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| 命令                             | 函数                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | 生成 .NET Core 应用程序。                                     |
| [dotnet clean](dotnet-clean.md)     | 清除生成输出。                                              |
| [dotnet help](dotnet-help.md)       | 显示命令更详细的在线文档。           |
| [dotnet migrate](dotnet-migrate.md) | 将有效的预览版 2 项目迁移到 .NET Core SDK 1.0 项目。  |
| [dotnet msbuild](dotnet-msbuild.md) | 提供对 MSBuild 命令行的访问权限。                        |
| [dotnet new](dotnet-new.md)         | 为给定的模板初始化 C# 或 F# 项目。                |
| [dotnet pack](dotnet-pack.md)       | 创建代码的 NuGet 包。                               |
| [dotnet publish](dotnet-publish.md) | 发布 .NET 依赖于框架或独立应用程序。 |
| [dotnet restore](dotnet-restore.md) | 还原给定应用程序的依赖项。                  |
| [dotnet run](dotnet-run.md)         | 从源运行应用程序。                                   |
| [dotnet sln](dotnet-sln.md)         | 用于添加、删除和列出解决方案文件中项目的选项。       |
| [dotnet store](dotnet-store.md)     | 将程序集存储到运行时包存储区。                     |
| [dotnet test](dotnet-test.md)       | 使用测试运行程序运行测试。                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| 命令                             | 函数                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | 生成 .NET Core 应用程序。                                     |
| [dotnet clean](dotnet-clean.md)     | 清除生成输出。                                              |
| [dotnet migrate](dotnet-migrate.md) | 将有效的预览版 2 项目迁移到 .NET Core SDK 1.0 项目。  |
| [dotnet msbuild](dotnet-msbuild.md) | 提供对 MSBuild 命令行的访问权限。                        |
| [dotnet new](dotnet-new.md)         | 为给定的模板初始化 C# 或 F# 项目。                |
| [dotnet pack](dotnet-pack.md)       | 创建代码的 NuGet 包。                               |
| [dotnet publish](dotnet-publish.md) | 发布 .NET 依赖于框架或独立应用程序。 |
| [dotnet restore](dotnet-restore.md) | 还原给定应用程序的依赖项。                  |
| [dotnet run](dotnet-run.md)         | 从源运行应用程序。                                   |
| [dotnet sln](dotnet-sln.md)         | 用于添加、删除和列出解决方案文件中项目的选项。       |
| [dotnet test](dotnet-test.md)       | 使用测试运行程序运行测试。                                     |

---

### <a name="project-references"></a>项目引用

命令 | 函数
--- | ---
[dotnet add reference](dotnet-add-reference.md) | 添加项目引用。
[dotnet list reference](dotnet-list-reference.md) | 列出项目引用。
[dotnet remove reference](dotnet-remove-reference.md) | 删除项目引用。

### <a name="nuget-packages"></a>NuGet 包

命令 | 函数
--- | ---
[dotnet add package](dotnet-add-package.md) | 添加 NuGet 包。
[dotnet remove package](dotnet-remove-package.md) | 删除 NuGet 包。

### <a name="nuget-commands"></a>NuGet 命令

命令 | 函数
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | 从服务器删除或取消列出包。
[dotnet nuget locals](dotnet-nuget-locals.md) | 清除或列出本地 NuGet 资源，例如 http 请求缓存、临时缓存或计算机范围的全局包文件夹。
[dotnet nuget push](dotnet-nuget-push.md) | 将包推送到服务器，并将其发布。

### <a name="global-tools-commands"></a>全局工具命令

[.NET Core 全局工具](global-tools.md)可与 .NET Core SDK 2.1.300 一起开始使用：

命令 | 函数
--- | ---
[dotnet tool install](dotnet-tool-install.md) | 在计算机上安装全局工具。
[dotnet tool list](dotnet-tool-list.md) | 列出当前安装在计算机上的默认目录中或指定路径中的所有全局工具。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | 从计算机中卸载全局工具。
[dotnet tool update](dotnet-tool-update.md) | 在计算机上更新全局工具。

### <a name="additional-tools"></a>其他工具

自 .NET Core SDK 2.1.300 开始，许多使用 `DotnetCliToolReference` 的仅在每个项目的基础上可用的工具现作为 .NET Core SDK 的一部分提供。 下表中列出了这些工具：

| 工具                                              | 函数                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 创建和管理开发证书。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core 命令行工具。                    |
| sql-cache                                         | SQL Server 缓存命令行工具。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 管理开发用户机密。                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | 启动文件观察程序，以在更改文件时运行命令。 |

有关每个工具的详细信息，请键入 `dotnet <tool-name> --help`。

## <a name="examples"></a>示例

创建新的 .NET Core 控制台应用程序：

`dotnet new console`

还原给定应用程序的依赖项：

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

生成给定目录中的项目及其依赖项：

`dotnet build`

运行应用程序 DLL，如 `myapp.dll`：

`dotnet myapp.dll`

## <a name="environment-variables"></a>环境变量

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

主包缓存。 如果未设置，则默认为 Unix 上的 `$HOME/.nuget/packages` 或 Windows 上的 `%HOME%\NuGet\Packages`。

`DOTNET_SERVICING`

指定加载运行时期间共享主机要使用的服务索引的位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集并向 Microsoft 发送 .NET Core 工具使用情况的相关数据。 设置为 `true` 以选择退出遥测功能（接受的值为 `true`、`1` 或 `yes`）。 否则，设置为 `false` 以选择加入遥测功能（接受的值为 `false`、`0` 或 `no`）。 如果未设置，则默认为 `false` 且遥测功能为活动状态。

`DOTNET_MULTILEVEL_LOOKUP`

指定是否从全局位置解析 .NET Core 运行时、共享框架或 SDK。 如果未设置，则默认为 `true`。 设置为 `false` 不从全局位置解析，并且具有独立的 .NET Core 安装（接受的值为 `0` 或 `false`）。 有关多级别查找的详细信息，请参阅 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)（多级别 SharedFX 查找）。

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

如果设置为 `0`，则禁用次要版本前滚。 有关详细信息，请参阅[前滚](../whats-new/dotnet-core-2-1.md#roll-forward)。

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

主包缓存。 如果未设置，则默认为 Unix 上的 `$HOME/.nuget/packages` 或 Windows 上的 `%HOME%\NuGet\Packages`。

`DOTNET_SERVICING`

指定加载运行时期间共享主机要使用的服务索引的位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集并向 Microsoft 发送 .NET Core 工具使用情况的相关数据。 设置为 `true` 以选择退出遥测功能（接受的值为 `true`、`1` 或 `yes`）。 否则，设置为 `false` 以选择加入遥测功能（接受的值为 `false`、`0` 或 `no`）。 如果未设置，则默认为 `false` 且遥测功能为活动状态。

`DOTNET_MULTILEVEL_LOOKUP`

指定是否从全局位置解析 .NET Core 运行时、共享框架或 SDK。 如果未设置，则默认为 `true`。 设置为 `false` 不从全局位置解析，并且具有独立的 .NET Core 安装（接受的值为 `0` 或 `false`）。 有关多级别查找的详细信息，请参阅 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)（多级别 SharedFX 查找）。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

主包缓存。 如果未设置，则默认为 Unix 上的 `$HOME/.nuget/packages` 或 Windows 上的 `%HOME%\NuGet\Packages`。

`DOTNET_SERVICING`

指定加载运行时期间共享主机要使用的服务索引的位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

指定是否收集并向 Microsoft 发送 .NET Core 工具使用情况的相关数据。 设置为 `true` 以选择退出遥测功能（接受的值为 `true`、`1` 或 `yes`）。 否则，设置为 `false` 以选择加入遥测功能（接受的值为 `false`、`0` 或 `no`）。 如果未设置，则默认为 `false` 且遥测功能为活动状态。

---
