---
title: .NET Core 应用程序部署
description: 了解有关部署 .NET Core 应用程序的方式。
author: rpetrusha
ms.author: ronpet
ms.date: 12/03/2018
ms.custom: seodec18
ms.openlocfilehash: 6f88659fcef49eba9344d3c4b2f0245b4072d7ab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745442"
---
# <a name="net-core-application-deployment"></a>.NET Core 应用程序部署

可以为 .NET Core 应用程序创建三种部署：

- 依赖框架的部署。 顾名思义，依赖框架的部署 (FDD) 依赖目标系统上存在共享系统级版本的 .NET Core。 由于已存在 .NET Core，因此应用在 .NET Core 安装程序间也是可移植的。 应用仅包含其自己的代码和任何位于 .NET Core 库外的第三方依赖项。 FDD 包含可通过在命令行中使用 [dotnet 实用程序](../tools/dotnet.md)启动的 *.dll* 文件。 例如，`dotnet app.dll` 就可以运行一个名为 `app` 的应用程序。

- 独立部署。 与 FDD 不同，独立部署 (SCD) 不依赖目标系统上存在的共享组件。 所有组件（包括 .NET Core 库和 .NET Core 运行时）都包含在应用程序中，并且独立于其他 .NET Core 应用程序。 SCD 包括一个可执行文件（如 Windows 平台上名为 `app` 的应用程序的 app.exe），它是特定于平台的 .NET Core 主机的重命名版本，还包括一个 .dll 文件（如 app.dll），而它是实际的应用程序。

- 依赖框架的可执行文件。 生成在目标平台上运行的可执行文件。 类似于 FDD，依赖框架的可执行文件 (FDE) 是特定于平台的，而不是自包含的。 这些部署的运行仍依赖于现有的 .NET Core 共享系统级版本。 与 SCD 不同，应用仅包含代码和任何位于 .NET Core 库外的第三方依赖项。 FDE 生成在目标平台上运行的可执行文件。

## <a name="framework-dependent-deployments-fdd"></a>依赖框架的部署 (FDD)

对于 FDD，仅部署应用程序和第三方依赖项。 应用将使用目标系统上存在的 .NET Core 版本。 这是定目标到 .NET Core 的 .NET Core 和 ASP.NET Core 应用程序的默认部署模型。

### <a name="why-create-a-framework-dependent-deployment"></a>为什么创建依赖框架的部署？

部署 FDD 具有很多优点：

- 不需要提前定义 .NET Core 应用将在其上运行的目标操作系统。 因为无论什么操作系统，.NET Core 的可执行文件和库都是用通用的 PE 文件格式，因此，无论什么基础操作系统，.NET Core 都可执行应用。 有关 PE 文件格式的详细信息，请参阅 [.NET 程序集文件格式](../../standard/assembly/file-format.md)。

- 部署包很小。 只需部署应用及其依赖项，而无需部署 .NET Core 本身。

- 除非重写，否则 FDD 将使用目标系统上安装的最新服务运行时。 这允许应用程序使用 .NET Core 运行时的最新修补版本。 

- 许多应用都可使用相同的 .NET Core 安装，从而降低了主机系统上磁盘空间和内存使用量。

也有几个缺点：

- 仅当主机系统上已安装应用设为目标的 .NET Core 版本[或更高版本](../versions/selection.md#framework-dependent-apps-roll-forward)时，应用才能运行。

- 如果不了解将来版本，.NET Core 运行时和库可能发生更改。 在极少数情况下，这可能会更改应用的行为。

## <a name="self-contained-deployments-scd"></a>独立部署 (SCD)

对于独立部署，可以部署应用和所需的第三方依赖项以及生成应用所使用的 .NET Core 版本。 创建 SCD 不包括各种平台上的 [.NET Core 本机依赖项](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)，因此运行应用前这些依赖项必须已存在。 有关在运行时进行版本绑定的详细信息，请参阅有关 [.NET Core 中的版本绑定](../versions/selection.md)的文章。

从 NET Core 2.1 SDK（版本 2.1.300）开始，.NET Core 支持修补程序版本前滚。 在创建独立部署时，.NET Core 工具会自动包含你的应用程序所指向的 .NET Core 版本的最新服务的运行时。 （最新服务的运行时包括安全修补程序和其他 bug 修复程序。）服务的运行时不需要存在于你的生成系统上；它会从 NuGet.org 自动下载。有关详细信息，包括有关如何选择退出修补程序版本前滚的说明，请参阅[独立部署运行时前滚](runtime-patch-selection.md)。

FDD 和 SCD 部署使用单独的主机可执行文件，使你可以使用发布者签名为 SCD 签署主机可执行文件。

### <a name="why-deploy-a-self-contained-deployment"></a>为什么要部署独立部署？

部署独立部署主要有两个优点：

- 可以对与应用一起部署的 .NET Core 版本具有单独的控制权。 只有你才能维护 .NET Core。

- 请放心，目标系统可以运行你的 .NET Core 应用，因为你提供的是应用将在其上运行的 .NET Core 版本。

它也有几个缺点：

- 由于 .NET Core 包含在部署包中，因此必须提前选择为其生成部署包的目标平台。

- 部署包相对较大，因为需要将 .NET Core 和应用及其第三方依赖项包括在内。

  从.NET Core 2.0 开始，可以通过使用 .NET Core [*全球化固定模式*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)在 Linux 系统上减少大约 28 MB 的部署大小。 通常，Linux 上的 .NET Core 依赖于 [ICU 库](http://icu-project.org)来实现全球化支持。 在固定模式下，库不包含在部署中，并且所有区域性的行为均类似于[固定区域性](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)。

- 向系统部署大量独立的 .NET Core 应用可能会使用大量磁盘空间，因为每个应用都会复制 .NET Core 文件。

## <a name="framework-dependent-executables-fde"></a>依赖框架的可执行文件 (FDE)

从 .NET Core 2.2 开始，可以将应用程序部署为 FDE，以及所需的第三方依赖项。 应用将使用目标系统上安装的 .NET Core 版本。

### <a name="why-deploy-a-framework-dependent-executable"></a>为什么要部署依赖框架的可执行文件？

部署 FDE 具有很多优点：

- 部署包很小。 只需部署应用及其依赖项，而无需部署 .NET Core 本身。

- 许多应用都可使用相同的 .NET Core 安装，从而降低了主机系统上磁盘空间和内存使用量。

- 应用程序无需调用 `dotnet` 实用程序，可以通过调用已发布的可执行文件直接运行。

也有几个缺点：

- 仅当主机系统上已安装应用设为目标的 .NET Core 版本[或更高版本](../versions/selection.md#framework-dependent-apps-roll-forward)时，应用才能运行。

- 如果不了解将来版本，.NET Core 运行时和库可能发生更改。 在极少数情况下，这可能会更改应用的行为。

- 必须为每个目标平台发布应用。

## <a name="step-by-step-examples"></a>分步示例

有关使用 CLI 工具部署 .NET Core 应用的分步示例，请参阅[使用 CLI 工具部署 .NET Core 应用](deploy-with-cli.md)。 有关使用 Visual Studio 部署 .NET Core 应用的分步示例，请参阅 [使用 Visual Studio 部署 .NET Core 应用](deploy-with-vs.md)。 

## <a name="see-also"></a>请参阅

- [使用 CLI 工具部署 .NET Core 应用程序](deploy-with-cli.md)
- [使用 Visual Studio 部署 .NET Core 应用程序](deploy-with-vs.md)
- [包、元包和框架](../packages.md)
- [.NET Core 运行时标识符 (RID) 目录](../rid-catalog.md)
