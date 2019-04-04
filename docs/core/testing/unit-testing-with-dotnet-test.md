---
title: 使用 dotnet test 和 xUnit 在 .NET Core 中进行 C# 代码单元测试
description: 通过使用 dotnet test 和 xUnit 分步生成示例解决方案的交互体验，了解 C# 和 .NET Core 中的单元测试概念。
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 97cf42c78154375ce06639d4a3029ed87b993ced
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504348"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>使用 dotnet test 和 xUnit 在 .NET Core 中进行 C# 单元测试

本教程介绍分步构建示例解决方案的交互式体验，以了解单元测试概念。 如果希望使用预构建解决方案学习本教程，请在开始前[查看或下载示例代码](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)。 有关下载说明，请参阅[示例和教程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="creating-the-source-project"></a>创建源项目

打开 shell 窗口。 创建一个名为 *unit-testing-using-dotnet-test* 的目录，以保留该解决方案。
在此新目录中，运行 [`dotnet new sln`](../tools/dotnet-new.md) 创建新的解决方案。 通过解决方案，可轻松管理类库和单元测试项目。
在解决方案目录中，创建 PrimeService 目录。 现在，目录和文件结构应如下所示：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

将 *PrimeService* 作为当前目录，然后运行 [`dotnet new classlib`](../tools/dotnet-new.md) 以创建源项目。 将 *Class1.cs* 重命名为 *PrimeService.cs*。 首先创建 `PrimeService` 类的失败实现：

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

将目录更改回 unit-testing-using-dotnet-test 目录。

运行 [dotnet sln](../tools/dotnet-sln.md) 命令，向解决方案添加类库项目：

```
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>创建测试项目

接下来，创建 PrimeService.Tests 目录。 下图显示了它的目录结构：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

将 *PrimeService.Tests* 目录作为当前目录，并使用 [`dotnet new xunit`](../tools/dotnet-new.md) 创建一个新项目。 此命令会创建将 [xUnit](https://xunit.github.io/) 用作测试库的测试项目。 生成的模板在 PrimeServiceTests.csproj 文件中配置测试运行程序，类似以下代码：

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

测试项目需要其他包创建和运行单元测试。 `dotnet new` 在以前的步骤中已添加 xUnit 和 xUnit 运行程序。 现在，将 `PrimeService` 类库作为另一个依赖项添加到项目中。 使用 [`dotnet add reference`](../tools/dotnet-add-reference.md) 命令：

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

可以在 GitHub 上的[示例存储库](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)中看到整个文件。

下面显示的是最终的解决方案布局：

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

若要向解决方案添加测试项目，请在 unit-testing-using-dotnet-test 目录下运行 [dotnet sln](../tools/dotnet-sln.md) 命令：

```
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>创建第一个测试

编写一个失败测试，使其通过，然后重复此过程。 从 PrimeService.Tests 目录删除 UnitTest1.cs，并创建一个名为 PrimeService_IsPrimeShould.cs 的新 C# 文件。 添加以下代码：

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` 属性指示由测试运行程序运行的测试方法。 在 PrimeService.Tests 文件夹中，执行 [`dotnet test`](../tools/dotnet-test.md)，以生成测试和类库，然后运行测试。 xUnit 测试运行程序包含要运行测试的程序入口点。 `dotnet test` 使用已创建的单元测试项目启动测试运行程序。

测试失败。 尚未创建实现。 在起作用的 `PrimeService` 类中编写最简单的代码，使此测试通过。 将现有的 `IsPrime` 方法实现替换为以下代码：

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

在 *PrimeService.Tests* 目录中，再次运行 `dotnet test`。 `dotnet test` 命令构建 `PrimeService` 项目，然后构建 `PrimeService.Tests` 项目。 构建这两个项目后，该命令将运行此单项测试。 测试通过。

## <a name="adding-more-features"></a>添加更多功能

你已经通过了一个测试，现在可以编写更多测试。 质数有其他几种简单情况：0、-1。 可以将这些情况添加为具有 `[Fact]` 属性的新测试，但这很快就会变得枯燥乏味。 还有其他 xUnit 属性，可使你编写类似测试套件：

- `[Theory]` 表示执行相同代码，但具有不同输入参数的测试套件。

- `[InlineData]` 属性指定这些输入的值。

可应用这两个属性（`[Theory]` 和 `[InlineData]`）在 PrimeService_IsPrimeShould.cs 文件中创建单一理论，而不是创建新测试。 此索引是测试多个小于 2（即最小的质数）的值的方法：

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

再次运行 `dotnet test`，其中两个测试应失败。 若要使所有测试通过，可以在 PrimeService.cs 文件中更改 `IsPrime` 方法开头的 `if` 子句：

```csharp
if (candidate < 2)
```

通过在主库中添加更多测试、理论和代码继续循环访问。 你将拥有[已完成的测试版本](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)和[库的完整实现](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)。

### <a name="additional-resources"></a>其他资源

- [xUnit.net 官方网站](https://xunit.github.io)
- [ASP.NET Core 中的测试控制器逻辑](/aspnet/core/mvc/controllers/testing)
