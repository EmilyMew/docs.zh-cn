---
title: .NET Framework 和带外版本
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c70382b0d74e830610d1cd7746fd14244b829a0
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654557"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>.NET Framework 和带外版本

.NET Framework 不断适应不同的平台（例如 Windows Phone 和 Windows 应用商店应用以及传统桌面和 Web 应用）以最大化代码的重复使用。 除了 .NET Framework 定期发布之外，我们还会发布处于预发布阶段 (OOB) 的新功能以改善跨平台开发或引入新功能。 本主题讨论 .NET Framework 及其 OOB 版本的未来方向。

## <a name="advantages-of-oob-releases"></a>OOB 版本的优点
 将新组件或更新发送给带区之外的组件让 Microsoft 能够更频繁地提供 .NET Framework 的更新。 此外，我们可以更快地收集和回应客户反馈。

 如果你在应用程序中使用了 OOB 功能，你的用户不必安装最新版 .NET Framework 即可运行你的应用程序，因为 OOB 程序集是与你的应用程序包一起部署的。

## <a name="how-oob-packages-are-distributed"></a>OOB 包是如何存储的
核心公共语言运行时 (CLR) 组件的 OOB 版本通过 [NuGet ](https://www.nuget.org/)（.NET 的包管理器）提供。 NuGet 让你可以轻松地通过 Visual Studio 中的解决方案资源管理器浏览并将库添加至你的 .NET Framework 项目。 从 Visual Studio 2012 开始，NuGet 随附于 Visual Studio 的所有版本。 若要确定 NuGet 是否已安装，请在 Visual Studio“工具”菜单上查找“NuGet 包管理器”。 如果尚未安装：

1.  在 Visual Studio 菜单栏中，依次选择“工具”和“扩展和更新”（在 Visual Studio 2010 中，选择“扩展管理器”）。

     此时，“扩展和更新”对话框打开。

2.  依次选择“联机”、“NuGet 包管理器”和“下载”。

3.  在下载完毕后，重新启动 Visual Studio。

 有关详细安装说明，请参阅 NuGet 文档网站上的[安装 NuGet](/nuget/install-nuget-client-tools)。 有关 NuGet 的详细信息，请参阅 [NuGet 文档](/nuget)。

## <a name="using-a-nuget-oob-package"></a>使用 NuGet OOB 程序包
 在安装 NuGet 后，可以使用 Visual Studio 中的解决方案资源管理器浏览并添加引用到 NuGet 程序包：

1.  在 Visual Studio 中打开项目的快捷菜单，然后选择“管理 NuGet 包”。 （也可以在“项目”菜单中选择此选项。）

2.  在左侧窗格中，选择“联机”。

3.  如果要使用预发行包，请选择中间窗格内下拉列表框中的“包括预发行版”（而不选择“仅限稳定版”）。

4.  在右侧窗格中，使用“搜索”框来查找要使用的包。 某些 Microsoft 程序包通过 Microsoft .NET Framework 徽标进行识别，发布者均为 Microsoft。

 ![显示 NuGet 包管理器的屏幕截图。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

 如前所述，当你部署使用了 OOB 包的应用程序，OOB 程序集将随附你的应用程序包。

## <a name="types-of-oob-releases"></a>OOB 版本的类型
 通常情况下，OOB 程序包具有一个或多个预发行版本和一个稳定的版本。 预发行附带的许可证通常不允许再发行，但可让你试用程序包并提供反馈。 任何对包的更新中都包含反馈。 最终发布版本作为稳定的包随 NuGet 分发并包含允许随应用程序重新分发 NuGet 程序包的许可证。 稳定程序包受 Microsoft 支持。 Microsoft 还提供 IntelliSense 支持以及其他文档类型（如所有程序包的博客文章和论坛答案）。 此外，只有一些程序包可使用源代码，并非所有程序包都可使用。 有关新增和更新后的包的公告，可订阅 [.NET Framework 博客](https://devblogs.microsoft.com/dotnet/)。

 若要查找预发行版包和稳定版包，请在 NuGet 包管理器中选择“包括预发行版”。

 如果要接收稳定版包的通知，请订阅 [.NET Framework 源](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)。

## <a name="see-also"></a>请参阅

- [入门](../../../docs/framework/get-started/index.md)