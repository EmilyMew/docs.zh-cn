---
title: 将 WPF 应用移植到 .NET Core 3.0
description: 介绍如何将 .NET Framework Windows Presentation Foundation 应用程序移植到适用于 Windows 的 .NET Core 3.0。
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 29ea308ee5147cfb18df312887e933615e349803
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58677545"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>如何：将 WPF 桌面应用移植到 .NET Core

本文介绍如何将基于 Windows Presentation Foundation (WPF) 的桌面应用从 .NET Framework 移植到 .NET Core 3.0。 .NET Core 3.0 SDK 支持 WPF 应用程序。 WPF 仍是仅适用于 Windows 的框架，并且只能在 Windows 上运行。 示例使用 .NET Core SDK CLI 创建和管理项目。

本文中的各种名称用于标识迁移所用的文件类型。 迁移项目时，你的文件将以不同的名称命名，因此，请自行在心里将它们与下面列出的文件进行匹配：

| 文件 | 说明 |
| ---- | ----------- |
| **MyApps.sln** | 解决方案文件的名称。 |
| **MyWPF.csproj** | 要移植的 .NET Framework WPF 项目的名称。 |
| **MyWPFCore.csproj** | 创建的新 .NET Core 项目的名称。 |
| **MyAppCore.exe** | .NET Core WPF 应用可执行文件。 |

## <a name="prerequisites"></a>系统必备

- 适用于要执行的任何设计器工作的 [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core)。

  安装以下 Visual Studio 工作负载：
  - .NET 桌面开发
  - .NET 跨平台开发

- 在解决方案中顺利生成和运行的有效 WPF 项目。
- 项目必须使用 C# 进行编码。 
- 安装最新 [.NET Core 3.0](https://aka.ms/netcore3download) 预览版。


>[!NOTE]
>Visual Studio 2017 不支持 .NET Core 3.0 项目。 “Visual Studio 2019 预览版/RC”支持 .NET Core 3.0 项目，但尚不支持适用于 .NET Core 3.0 WPF 项目的可视化设计器。 要使用可视化设计器，解决方案中必须包含可与 .NET Core 项目共享其文件的 .NET WPF 项目。

### <a name="consider"></a>考虑

移植 .NET Framework WPF 应用程序时，必须考虑以下几个事项。

01. 检查应用程序是否适合迁移。

    使用 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)确定项目将会迁移到 .NET Core 3.0。 如果项目存在 .NET Core 3.0 相关问题，分析器可帮助你识别这些问题。

01. 使用的是不同版本的 WPF。

    发布 .NET Core 3.0 预览版 1 时，WPF 在 GitHub 上公布了开放源代码。 .NET Core WPF 的代码是 .NET Framework WPF 基本代码的一个分支。 可能存在一些差异导致应用程序无法移植。

01. 使用 [Windows 兼容包][compat-pack]可能有助于进行迁移。

    某些 API 可在 .NET Framework 中使用，但不可用于 .NET Core 3.0。 [Windows 兼容包][compat-pack] 增加了很多此类 API，有助于使 WPF 应用与 .NET Core 兼容。

01. 更新项目使用的 NuGet 包。

    在执行任何迁移之前使用最新版 NuGet 包始终是一个不错的做法。 如果应用程序引用任何 NuGet 包，请将它们更新到最新版本。 确保成功生成应用程序。 升级后，如果存在任何包错误，请将包降级到不会破坏代码的最新版本。

01. Visual Studio 2019 预览版/RC 尚不支持适用于 .NET Core 3.0 的 WPF 设计器

    目前，如果要从 Visual Studio 中使用 WPF 设计器，需要保留现有的 .NET Framework WPF 项目文件。

## <a name="create-a-new-sdk-project"></a>创建新的 SDK 项目

创建的新 .NET Core 3.0 项目必须位于不同于 .NET Framework 项目的目录中。 如果它们位于同一目录中，可能会与 obj 目录中生成的文件发生冲突。 本例中，你将在“SolutionFolder”目录中创建一个名为“MyWPFAppCore”的目录：

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

接下来，需要在“MyWPFAppCore”目录中创建“MyWPFCore.csproj”项目。 可以使用所选的文本编辑器手动创建此文件。 粘贴以下 XML：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

如果不想手动创建项目文件，可以使用 Visual Studio 或 .NET Core SDK 生成项目。 但是，必须删除项目模板生成的所有其他文件（项目文件除外）。 若要使用 SDK，请从 SolutionFolder 目录运行以下命令：

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

创建“MyWPFCore.csproj”后，目录结构应如下所示：

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

需要使用 Visual Studio 或“SolutionFolder”目录中的 .NET Core CLI 将“MyWPFCore.csproj”项目添加到“MyApps.sln”：

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>修复程序集信息生成

使用 .NET Framework 创建的 Windows Presentation Foundation 项目包含一个 `AssemblyInfo.cs` 文件，该文件包含诸如要生成的程序集的版本等程序集特性。 SDK 样式的项目会根据 SDK 项目文件自动生成此信息。 同时具有两种类型的“程序集信息”时，会产生冲突。 通过禁用自动生成可以解决此问题，这会强制项目使用现有的 `AssemblyInfo.cs` 文件。

若要添加到主 `<PropertyGroup>` 节点，有三个设置项。 

- **GenerateAssemblyInfo**\
将此属性设置为 `false` 时，它不会生成程序集特性。 这可以避免与 .NET Framework 项目中的现有 `AssemblyInfo.cs` 文件冲突。

- **AssemblyName**\
此属性的值是编译时创建的输出二进制。 该名称不需要添加扩展名。 例如，使用 `MyCoreApp` 生成 `MyCoreApp.exe`。

- **RootNamespace**\
项目使用的默认命名空间。 它应该与 .NET Framework 项目的默认命名空间匹配。

将这三个元素添加到 `MyWPFCore.csproj` 文件中的 `<PropertyGroup>` 节点：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>添加源代码
现在，“MyWPFCore.csproj”项目不编译任何代码。 默认情况下，.NET Core 项目会自动包含当前目录和所有子目录中的所有源代码。 必须使用相对路径配置项目以包含 .NET Framework 项目中的代码。 如果 .NET Framework 项目使用了“.resx”文件作为窗口和控件的图标和资源，则也需要包含这些文件。 

需要添加到项目中的第一个 `<ItemGroup>` 节点将包括“App.xaml”文件，该文件代表你的应用使用的启动配置和资源。 “App.xaml”文件还会附带“App.xaml.cs”文件，但它将自动包含在不同的 `<ItemGroup>` 中。

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

接下来，将以下 `<ItemGroup>` 节点添加到项目中。 每个语句都包含一个文件 glob 模式，其中包含子目录。 它包括项目的源代码、任何设置文件和任何资源。 将会显式排除“obj”目录。

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

接下来，包括另一个 `<ItemGroup>` 节点，该节点包含项目中每个“xaml”文件（“App.xaml”文件除外）的 `<Page>` 条目。 它们包含“xaml”格式的所有窗口、页面和资源。 不能在此处使用 glob 模式，必须为每个文件添加一个条目并指出使用的 `<Generator>`。

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>添加 NuGet 包

将 .NET Framework 项目引用的每个 NuGet 包添加到 .NET Core 项目。 

你的 .NET Framework WPF 应用很可能有一个“packages.config”文件，其中包含项目引用的所有 NuGet 包的列表。 可以查看此列表以确定要添加到 .NET Core 项目的 NuGet 包。 例如，如果 .NET Framework 项目引用了 `MahApps.Metro` NuGet 包，请使用 Visual Studio 将其添加到项目中。 还可以使用 Visual Studio 从 SolutionFolder 目录添加包引用：

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

之前的命令会将以下 NuGet 引用添加到 MyWPFCore.csproj 项目：

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>编译问题

如果在编译项目时遇到问题，可能是由于正在使用的一些仅适用于 Windows 的 API 在 .NET Framework 中可用，但在 .NET Core 中不可用。 可以尝试将 [Windows 兼容包][compat-pack] NuGet 包添加到项目中。 此包仅在 Windows 上运行，为 .NET Core 和 .NET Standard 项目添加了大约 20,000 个 Windows API。

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

上一个命令会将以下内容添加到 MyWPFCore.csproj 项目：

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>WPF 设计器

如本文所述，Visual Studio 2019 预览版/RC 仅支持 .NET Framework 项目中的 WPF 设计器。 通过创建并行 .NET Core 项目，可以在使用 .NET Framework 项目设计窗体时通过 .NET Core 测试项目。 解决方案文件包括 .NET Framework 和 .NET Core 项目。 在 .NET Framework 项目中添加和设计窗体和控件，并且根据添加到 .NET Core 项目的文件 glob 模式，任何新的或更改的文件将自动包含在 .NET Core 项目中。

一旦 Visual Studio 2019 支持 WPF 设计器，就可以将 .NET Core 项目文件的内容复制/粘贴到 .NET Framework 项目文件中。 然后删除使用 `<Source>` 和 `<EmbeddedResource>` 项添加的文件 glob 模式。 修复由应用程序使用的任何项目引用的路径。 这可以有效地将 .NET Framework 项目升级到 .NET Core 项目。
 
## <a name="next-steps"></a>后续步骤

* 详细了解 [Windows 兼容包][compat-pack]。
* 观看关于将 .NET Framework WPF 项目移植到 .NET Core 的[视频](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt)。

[compat-pack]: windows-compat-pack.md
