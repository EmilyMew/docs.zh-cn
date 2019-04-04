---
title: 如何：确定已安装的 .NET Framework 版本
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c4ad3ca5694457637a82a36c8db4534df43a9d7
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504426"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>如何：确定已安装的 .NET Framework 版本

用户可在他们的计算机上[安装](https://docs.microsoft.com/dotnet/framework/install)和运行 .NET Framework 的多个版本。 当你开发或部署应用时，你可能需要知道用户的计算机上安装了哪些 .NET Framework 版本。 

.NET Framework 由两个采用不同版本的主要组件构成：  
  
- 一组程序集，它们是为应用提供功能的类型与资源的集合。 .NET Framework 和程序集使用相同的版本号。  
  
- 公共语言运行时 (CLR)，可管理并执行应用的代码。 CLR 由其自己的版本号标识（请参阅[版本和依赖关系](~/docs/framework/migration-guide/versions-and-dependencies.md)）。  

> [!NOTE]
> 每个新版本的 .NET Framework 都会保留早期版本中的功能并会添加新功能。 可在同一台计算机上同时加载多个版本的 .NET Framework，这意味着可安装 .NET Framework 而无需卸载以前的版本。 通常，你不应卸载以前版本的 .NET Framework，因为你使用的应用程序可能依赖于特定版本，如果删除该版本，可能会中断。
>
> .NET Framework 版本和 CLR 版本之间存在差异： 
> - .NET Framework 版本基于构成 .Net Framework 类库的一组程序集。 例如，.NET Framework 版本包括 4.5、4.6.1 和 4.7.2。 
>- CLR 版本基于 .NET Framework 应用程序执行的运行时。 单个 CLR 版本通常可支持多个 .NET Framework 版本。 例如，CLR 版本 4.0.30319.xxxxx 支持 .NET Framework 版本 4 到 4.5.2，而 CLR 版本 4.0.30319.42000 支持从 .NET Framework 4.6 开始的 .NET Framework 版本。 
>
> 有关版本的详细信息，请参见 [.NET Framework 版本和依赖关系](versions-and-dependencies.md)。


若要获取计算机上安装的 .NET Framework 版本列表，请访问注册表。 可使用注册表编辑器查看注册表或使用代码进行查询：
 
- 查找较新的 .NET Framework 版本（4.5 及更高版本）： 
     - [使用注册表编辑器查找 .NET Framework 版本](#net_b)  
     - [使用代码查询注册表以获取 .NET Framework 版本](#net_d)  
     - [使用 PowerShell 查询注册表以获取 .NET Framework 版本](#ps_a)
- 查找较旧的 .NET Framework 版本 (1&#8211;4)：
     - [使用注册表编辑器查找 .NET Framework 版本](#net_a)
     - [使用代码查询注册表以获取 .NET Framework 版本](#net_c)   

若要获取计算机上安装的 CLR 版本列表，请使用工具或代码：  
  
- [使用 Clrver 工具](#clr_a)  
- [使用代码查询 Environment 类](#clr_b)  

有关检测安装的每个 .NET Framework 版本的更新的信息，请参阅[如何：确定已安装的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a>查找较新的 .NET Framework 版本（4.5 及更高版本）

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>在注册表中查找 .NET Framework 4.5 及更高版本

1. 在“开始”菜单中，选择“运行”，输入 regedit，然后选择“确定”。

     必须具有管理凭据才能运行 regedit。

2. 在注册表编辑器中，打开以下子项：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. 如果“完整”子项不存在，则表示尚未安装 .NET Framework 4.5 或更高版本。

    > [!NOTE]
    > 注册表中的“.NET Framework 安装程序”文件夹不以句点开头。

3. 请检查名为“Release”的 DWORD 条目。 如果存在，则安装 .NET Framework 4.5 或更高版本。 其值是对应于特定版本的 .NET Framework 的版本密钥。 以下图为例，“Release”条目的值为 378389，这是 .NET Framework 4.5 的版本密钥。 

     ![.NET Framework 4.5 的注册表项](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")

下表列出每个 .NET Framework 版本“Release”条目的最小值。 可以使用这些值，如下所示：

- 若要确定是否存在 .NET Framework 最低版本，测试在注册表中找到的“Release”DWORD 值是大于还是等于表中列出的值。 例如，如果应用程序需要 .NET Framework 4.7 或更高版本，则测试最小版本密钥值是否为 460798。

- 若要测试多个版本，请从最新的 .NET Framework 版本开始，然后对每个后续的早期版本进行测试。

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|.NET Framework 版本|Release DWORD 的值|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

有关完整的适用于特定 Windows 操作系统版本的 .NET Framework 的版本密钥表，请参阅 [.NET Framework 版本密钥和 Windows 操作系统版本](release-keys-and-os-versions.md)。


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a>使用代码查找 .NET Framework 4.5 及更高版本

1. 使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法访问 Windows 注册表中的“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full”子项。

    “HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full”子项中存在“Release”DWORD 条目表示已在电脑上安装 .NET Framework 4.5 或更高版本。 

2. 检查“Release”条目的值以确定安装的版本。 为了向前兼容，可检查是否有一个值大于或等于 [.NET Framework 版本表](#version_table)中所列的值。

下例检查注册表中“Release”条目的值，以查找已安装的 .NET Framework 4.5 及更高版本：

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

此示例遵循版本检查的建议做法：

- 检查“Release”条目的值是否大于或等于已知版本密钥的值。

- 按从最新版本到最早版本的顺序检查。

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>使用 PowerShell 检查所需的 .NET Framework 的最低版本（4.5 或更高版本）

- 使用 PowerShell 命令检查“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full”子项的“Release”条目的值。

以下示例检查“Release”条目的值，以确定是否已安装 .NET Framework 4.6.2 或更高版本。 如果安装了此代码，则返回 `True`，否则返回 `False`。

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

若要检查不同的所需最低 .NET Framework 版本，请使用 [.NET Framework 版本表](#version_table)中的“Release”值替换这些示例中的 394802。

## <a name="find-older-net-framework-versions-182114"></a>查找较旧的 .NET Framework 版本 1&#8211;4

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a>在注册表中查找 .NET Framework 版本 1&#8211;4 
  
1. 在“开始”菜单中，选择“运行”，输入 regedit，然后选择“确定”。
  
    必须具有管理凭据才能运行 regedit。  

2. 在注册表编辑器中，打开以下子项：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**：  

    - 对于 .NET Framework 1.1 到 3.5 版，每个安装的版本都在“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP”子项下列为子项。 例如，“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5”。 版本号存储为版本子项的“Version”条目中的值。 
     
    - 对于 .NET Framework 4，“Version”条目位于“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client”或“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full”子项下，或同时位于这两个子项下。

    > [!NOTE]
    > 注册表中的“.NET Framework 安装程序”文件夹不以句点开头。

    下图显示了 .NET Framework 3.5 的子项及其“Version”条目。

    ![.NET Framework 3.5 的注册表项。](media/net-4-and-earlier.png ".NET Framework 3.5 及更早版本")

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a>使用代码查找 .NET Framework 版本 1&#8211;4

- 使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 类访问 Windows 注册表中的“HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP”子项。

以下示例查找已安装的 .NET Framework 1-4 1&#8211;4：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a>查找 CLR 版本
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a>使用 Clrver.exe 查找当前的 CLR 版本

使用 [CLR 版本工具 (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) 确定计算机上安装了哪些版本的 CLR：

- 从 [Visual Studio 的开发人员命令提示](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs)，输入 `clrver`。

    示例输出：

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a>使用 Environment 类查找当前的 CLR 版本

> [!IMPORTANT]
> 对于 .NET Framework 4.5 及更高版本，请勿使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 属性来检测 CLR 的版本。 而应按照[使用代码查找 .NET Framework 4.5 及更高版本](#net_d)中所述查询注册表。

1. 查询 <xref:System.Environment.Version?displayProperty=nameWithType> 属性以检索 <xref:System.Version> 对象。 

    返回的 `System.Version` 对象标识当前正在执行代码的运行时版本。 它不返回计算机上可能已安装的程序集版本或运行时的其他版本。

    对于 .NET Framework 版本 4,4.5、4.5.1 和 4.5.2，返回的 <xref:System.Version> 对象的字符串表示形式为 4.0.30319. xxxxx 。 对于 .NET Framework 4.6 及更高版本，它的格式为 4.0.30319.42000。    

2. 获得 `Version` 对象后，按如下方式查询：

   - 对于主要版本标识符（例如，4 表示版本 4.0），请使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 属性。

   - 对于次要版本标识符（例如，0 表示版本 4.0），请使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 属性

   - 对于整个版本字符串（例如，4.0.30319.18010），请使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。 此方法返回一个值，该值反映正在执行代码的运行时的版本。 它不返回可能安装在计算机上的程序集版本或其他运行时版本。



以下示例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 属性检索 CLR 版本信息：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>请参阅

- [如何：确定安装了哪些 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)
- [安装面向开发者的 .NET Framework](../install/guide-for-developers.md)
- [.NET Framework 版本和依赖关系](versions-and-dependencies.md)
