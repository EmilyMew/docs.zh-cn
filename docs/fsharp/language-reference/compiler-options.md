---
title: 编译器选项
description: 使用F#编译器命令行选项来控制编译的应用F#应用程序和库。
ms.date: 12/10/2018
ms.openlocfilehash: fa639fe37ed336ad9f990e01bf2645c5a86498e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089752"
---
# <a name="compiler-options"></a>编译器选项

本主题介绍有关编译器命令行选项F#编译器、 fsc.exe。 此外可以通过设置项目属性控制编译环境。

## <a name="compiler-options-listed-alphabetically"></a>按字母顺序列出的编译器选项
下表显示了按字母顺序列出的编译器选项。 某些F#编译器选项都类似于C#编译器选项。 如果出现这种情况，一个指向C#编译器选项主题提供。

|编译器选项|描述|
|---------------|-----------|
|`-a filename.fs`|从指定的文件生成一个库。 此选项是一种简短形式`--target:library filename.fs`。|
|`--baseaddress:address`|指定要加载 DLL 的首选基址。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;baseaddress &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx)。|
|`--codepage:id`|指定要使用在编译期间，如果所需的页面不是系统的当前默认代码页的代码页。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;代码页的&#40;C&#35;编译器选项&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md)。|
|`--consolecolors`|指定错误和警告的控制台上使用彩色编码的文本。|
|`--crossoptimize[+|-]`|启用或禁用跨模块优化。|
|<code>--delaysign[+&#124;-]</code>|延迟签名程序集使用仅强名称密钥的公共部分。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;delaysign &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx)。|
|<code>--checked[+&#124;-]</code>|启用或禁用溢出检查的生成。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;检查&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx)。|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|启用或禁用生成调试信息或指定要生成的类型。 默认值为 full，允许附加到正在运行的程序。 选择**pdbonly**获取有限的 pdb （程序数据库） 文件中存储的调试信息。<br /><br />等效于C#具有相同名称的编译器选项。 有关详细信息，请参见<br /><br />[&#47;调试&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx)。|
|`--define:symbol`<br /><br />`-d:symbol`|定义条件编译中使用的符号。|
|<code>--deterministic[+&#124;-]</code>|生成具有确定性的程序集 （包括模块版本 GUID 以及时间戳）。 此选项不能用于通配符的版本号，且只支持嵌入和可移植调试类型|
|`--doc:xmldoc-filename`|指示编译器生成 XML 文档注释指定的文件。 有关更多信息，请参见 [XML Documentation](xml-documentation.md)。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;文档&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx)。|
|`--fullpaths`|指示编译器生成完全限定的路径。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;fullpaths &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/d315xc66.aspx)。|
|`--help`<br /><br />`-?`|显示用法信息，包括所有编译器选项的简短说明。|
|<code>--highentropyva[+&#124;-]</code>|启用或禁用高熵地址空间布局随机化 (ASLR) 增强的安全功能。 操作系统随机化内存中加载应用程序 （例如堆栈和堆） 的基础结构的位置的位置。 如果启用此选项，操作系统可以使用此随机化以在 64 位计算机上使用完整 64 位地址空间。|
|`--keycontainer:key-container-name`|指定强名称密钥容器。|
|`--keyfile:filename`|指定生成的程序集进行签名的公钥文件的名称。|
|`--lib:folder-name`<br /><br />`-I:folder-name`|指定要在其中搜索引用程序集的目录。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;lib &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx)。|
|`--linkresource:resource-info`|指定的资源链接到该程序集。 资源信息的格式 <code>filename[name[public&#124;private]]</code><br /><br />链接具有此选项的单个资源是嵌入整个资源文件的替代方法`--resource`选项。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;linkresource &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx)。|
|`--mlcompatibility`|将忽略所设计的功能用于与其他版本的 ML 兼容性时，将显示警告。|
|`--noframework`|禁用对.NET Framework 程序集的默认引用。|
|`--nointerfacedata`|指示编译器省略其通常向包含程序集的资源F#的特定元数据。|
|`--nologo`|在启动编译器时，不会显示横幅文本。|
|`--nooptimizationdata`|指示编译器将只包括所必需的实现内联的构造优化。 禁止跨模块内联，但会提高二进制兼容性。|
|`--nowin32manifest`|指示编译器省略默认的 Win32 清单。|
|`--nowarn:warning-number-list`|禁用按编号列出的特定警告。 用逗号分隔每个警告编号。 可以发现从编译输出的任何警告的警告编号。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;nowarn &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx)。|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|启用或禁用优化。 一些优化选项可以禁用或有选择地启用通过列出它们。 这些是： `nojitoptimize`， `nojittracking`， `nolocaloptimize`， `nocrossoptimize`， `notailcalls`。|
|`--out:output-filename`<br /><br />`-o:output-filename`|指定编译的程序集或模块的名称。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;out &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx)。|
|`--pdb:pdb-filename`|命名的输出调试 PDB （程序数据库） 文件。 此选项仅适用时`--debug`还启用了。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;pdb &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/ms228625.aspx)。|
|`--platform:platform-name`|指定生成的代码仅将在指定的平台上运行 (`x86`， `Itanium`，或`x64`)，或者，如果平台名称`anycpu`选择，指定生成的代码可以在任何平台上运行。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;平台&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx)。|
|`--preferreduilang:lang`| 指定首选的输出语言区域性名称 (例如， `es-ES`， `ja-JP`)。 |
|`--quotations-debug`|指定应派生自的表达式发出额外的调试信息F#的报价文本和反射的定义。 调试信息添加到自定义属性的F#表达式树节点。 请参阅[代码引用](code-quotations.md)并[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)。|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|使代码从F#或.NET Framework 程序集供正在编译的代码。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;引用&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx)。|
|`--resource:resource-filename`|将托管的资源文件嵌入到生成的程序集。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;资源&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx)。|
|`--sig:signature-filename`|生成基于生成的程序集的签名文件。 有关签名文件的详细信息，请参阅[签名](signatures.md)。|
|`--simpleresolution`|指定应使用基于目录的 Mono 规则而不是 MSBuild 解析解析程序集引用。 默认值是使用 MSBuild 解析，但在 Mono 下运行时例外。|
|`--standalone`|指定生成的程序集，包括所有依赖项使情况下独立运行而无需其他程序集，如F#库。|
|`--staticlink:assembly-name`|以静态方式链接给定的程序集和依赖于此程序集的所有引用的 Dll。 使用程序集名称，而不是 DLL 名称。|
|`--subsystemversion`|指定用于生成可执行文件的操作系统子系统的版本。 将 6.02 用于 Windows 8.1，6.01 用于 Windows 7，6.00 用于 Windows Vista。 此选项仅适用于可执行文件，而非 Dll，并且如果应用程序依赖于仅在某些版本的操作系统上可用的特定安全功能才需要使用。 如果使用此选项，并且用户尝试在较低版本的操作系统上执行应用程序，它将失败并显示错误消息。|
|<code>--tailcalls[+&#124;-]</code>|启用或禁用使用，尾 IL 指令将使得为尾递归函数重用堆栈帧。 默认情况下会启用此选项。|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|指定生成的已编译代码的类型和文件。<ul><li>`exe` 表示控制台应用程序。<br /></li><li>`winexe` 表示 Windows 应用程序，这不同于控制台应用程序，它不具有标准输入/输出流 （stdin、 stdout 和 stderr） 定义。<br /></li><li>`library` 是一个程序集没有入口点。<br /></li><li>`module` 是.NET Framework 模块 (.netmodule)，它可以更高版本结合，与其他模块到程序集。<br /></li><ul/>此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[&#47;目标&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx)。|
|`--times`|显示编译的计时信息。|
|`--utf8output`|启用打印编译器输出中的 utf-8 编码。|
|`--warn:warning-level`|设置警告等级 (0 到 5)。 默认级别为 3。 每个警告给定一个根据其严重性等级。 级别 5 程度在等级 1 提供更多，但更少的严重警告。<br /><br />5 级警告是：21 （在运行时检查递归使用），22 (`let rec`评估的顺序紊乱)，45 （完全的抽象） 和 52 （防御性副本）。 所有其他警告是级别 2。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;，则发出警告&#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx)。|
|`--warnon:warning-number-list`|启用默认情况下可能处于关闭状态，或通过另一个命令行选项禁用特定警告。 在F#3.0 中，只有 1182 （未使用的变量） 警告默认处于关闭状态。|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|启用或禁用警告报告为错误的选项。 你可以提供特定的警告编号，若要禁用或启用。 更高版本中命令行选项重写前面的命令行选项。 例如，若要指定不想报告为错误的警告，请指定`--warnaserror+` `--warnaserror-:warning-number-list`。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;warnaserror &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx)。|
|`--win32manifest:manifest-filename`|将 Win32 清单文件添加到编译。 此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;win32manifest &#40;C&#35;编译器选项&#41;](https://msdn.microsoft.com/library/bb545961.aspx)。|
|`--win32res:resource-filename`|将 Win32 资源文件添加到编译。<br /><br />此编译器选项等效于C#具有相同名称的编译器选项。 有关详细信息，请参阅[ &#47;win32res (&#40;C&#35;) 编译器选项&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx)。|

## <a name="related-articles"></a>相关文章

|标题|描述|
|-----|-----------|
|[F# Interactive 选项](fsharp-interactive-options.md)|介绍支持的命令行选项F#解释器、 fsi.exe。|
|[项目属性引用](/visualstudio/ide/reference/project-properties-reference)|介绍了项目，包括提供生成选项的项目属性页的 UI。|