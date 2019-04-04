---
title: .NET 中的程序集
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>.NET 中的程序集

程序集构成了 .NET 应用程序的部署、版本控制、重用、激活范围和安全权限的基本单元。 作为 .NET 应用程序 的构建基块，程序集采用可执行文件 (.exe) 或动态链接库文件 (.dll) 的形式。 它们向公共语言运行时提供了注意类型实现代码所需的信息。 可以将程序集视为一组构成功能逻辑单元并旨在配合使用的类型和资源。

在 .NET Core 和 .NET Framework 中，可以从一个或多个源代码文件生成程序集。 在 .NET Framework 中，程序集可以包含一个或多个模块。 因此，可以将大型项目规划为，由多个开发者单独开发各个源代码文件或模块，最后整合所有这些内容以创建一个程序集。 若要详细了解模块，请参阅[操作说明：生成多文件程序集](../../framework/app-domains/how-to-build-a-multifile-assembly.md)。

程序集具有以下属性：

- 程序集以 .exe 或 .dll 文件的形式实现。

- 对于面向 .NET Framework 的库，可以将程序集放入[全局程序集缓存](../../framework/app-domains/gac.md)，以便在应用程序之间共享程序集。 必须先为程序集命名强名称，然后才能将其添加到全局程序集缓存中。 有关详细信息，请参阅[具有强名称的程序集](../../framework/app-domains/strong-named-assemblies.md)。

- 只有在需要使用时才会将程序集加载到内存中。 如果不使用，就不会加载程序集。 也就是说，使用程序集，可以在大型项目中高效管理资源。

- 可以使用反射，以编程方式获取程序集的相关信息。 有关详细信息，请参阅[反射 (C#)](../../csharp/programming-guide/concepts/reflection.md) 或[反射 (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md)。

- 只能通过调用方法 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> 来加载程序集以检查它。

## <a name="assembly-manifest"></a>程序集清单

每个程序集中都有*程序集清单*。 与目录类似，程序集清单包含以下内容：

- 程序集的标识（名称和版本）。

- 文件表，描述构成程序集的其他所有文件（例如，.exe 或 .dll 文件依赖的所创建的其他程序集、位图或自述文件）。

- 程序集引用列表，列出了应用程序需要的可能由其他人创建的所有外部依赖项（.dll 或其他文件）。 程序集既可以引用全局对象，也可以引用私有对象。 全局对象可用于所有其他应用程序。 在 .NET Core 中，它们与特定的 .NET Core 运行时结合使用。 在 .NET Framework 中，它们位于全局程序集缓存中。 <xref:System.IO?displayProperty=nameWithType> 命名空间是全局程序集缓存中的程序集示例。 私有对象必须位于级别不高于应用程序安装目录的目录中。

由于程序集包含内容、版本控制和依赖项的相关信息，因此，使用它们的应用程序不依赖 Windows 注册表值也能正常运行。 程序集减少了 .dll 冲突，让应用程序变得更可靠、更易于部署。 在许多情况下，只需将 .NET 应用程序的文件复制到目标计算机，即可进行安装。 有关详细信息，请参阅[程序集清单](../../framework/app-domains/assembly-manifest.md)。

## <a name="adding-a-reference-to-an-assembly"></a>添加对程序集的引用

必须添加对程序集的引用，才能使用程序集。 接下来，可以对 C# 使用 [using 指令](../../csharp/language-reference/keywords/using-directive.md)，或者对 Visual Basic 使用 [Imports 语句](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)，从而选择要使用的项的命名空间。 引用和导入程序集后，应用程序可以使用其名称空间的所有可访问类型、属性、方法和其他成员，就好像它们的代码是源文件的一部分一样。

> [!NOTE]
> .NET 类库中的大多数程序集都是自动引用的。 但是，在某些情况下，系统程序集可能不会自动引用。 在 .NET Core 中，可以通过在 Visual Studio 中使用 NuGet 包管理器或者通过向 *.csproj 或 *.vbproj 项目添加程序集的 [\<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) 元素的方式，添加对包含该程序集的 NuGet 包的引用。 在 .NET Framework 中，可以通过在 Visual Studio 中使用“添加引用”对话框，或者通过使用 [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) 或 [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) 编译器的 `-reference` 命令行选项的方式，添加对该程序集的引用。

在 C# 中，还可以在单个应用程序中使用同一程序集的两个版本。 有关详细信息，请参阅[外部别名](../../csharp/language-reference/keywords/extern-alias.md)。

## <a name="creating-an-assembly"></a>创建程序集

编译应用程序有以下几种方式：在 Visual Studio 中生成程序集，使用 .NET Core 命令行界面 (CLI) 工具从命令行生成程序集，或者使用命令行编译器生成 .NET Framework 程序集。 要详细了解如何使用.NET CLI 工具生成程序集，请参阅 [.NET Core 命令行接口 (CLI) 工具](../../core/tools/index.md)。 要了解如何使用命令行编译器生成程序集，请参阅[使用 csc.exe 的命令行生成](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)（适用于 C#），以及[从命令行生成](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)（适用于 Visual Basic）。

> [!NOTE]
> 若要在 Visual Studio 中生成程序集，请选择“生成”菜单上的“生成”。

## <a name="see-also"></a>请参阅

- [.NET 程序集文件格式](file-format.md)
- [Assemblies in the Common Language Runtime](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)（公共语言运行时中的程序集）
- [友元程序集](friend-assemblies.md)
- [如何：加载和卸载程序集 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [如何：加载和卸载程序集 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [如何：在 .NET Core 中使用和调试程序集可卸载性](unloadability-howto.md)
- [如何：确定文件是否为程序集 (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [如何：确定文件是否为程序集 (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
