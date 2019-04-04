---
title: 按类别列出的 Visual Basic 编译器选项
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 333bfb539fc375fd8f2dd170a187002fcf81ea2b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827362"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>按类别列出的 Visual Basic 编译器选项
Visual Basic 命令行编译器用作一种编译来自 Visual Studio 集成的开发环境 (IDE) 中的程序的替代方法。 下面是 Visual Basic 命令行编译器选项按功能分类排序的列表。  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>编译器输出  
  
|Option|用途|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|禁止显示编译器横幅信息。|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|显示使用 UTF-8 编码的编译器输出。|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|在编译期间输出其他信息。|  
|`-modulename:<string>`|指定源模块的名称|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|指定编译器输出的语言。|
  
## <a name="optimization"></a>优化  
  
|Option|用途|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|指定输出文件各节的对齐位置。|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|启用/禁用优化。|  
  
## <a name="output-files"></a>输出文件  
  
|Option|用途|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|处理 XML 文件的文档注释。|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|如果输入相同，则会导致编译器输出的程序集其二进制内容在整个编译中相同。|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|设置编译器从而以 [!INCLUDE[Compact](~/includes/compact-md.md)] 为目标。|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|指定输出目录。|  
|[/refonly](refonly-compiler-option.md)|输出仅引用程序集。|
|[/refout](refout-compiler-option.md)|指定引用程序集的输出路径。|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|指定输出的格式。|  
  
## <a name="net-assemblies"></a>.NET 程序集  
  
|Option|用途|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|使编译器让指定文件中的所有类型信息可供当前正在编译的项目使用。|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|指定程序集是完全签名的还是部分签名的。|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|从指定的程序集导入命名空间。|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|指定密钥对的密钥容器名称从而为程序集赋予强名称。|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|指定包含密钥或密钥对的文件从而为程序集赋予强名称。|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|指定引用的程序集的位置[-引用](../../../visual-basic/reference/command-line-compiler/reference.md)选项。|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|从程序集导入元数据。|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|指定模块所属程序集的名称。|  
|`-analyzer`|从此程序集（缩写形式：-a）运行分析器|  
|`-additionalfile`|命名其他文件，这些文件不会直接影响代码生成，但可能由分析器用于生成错误或警告。|  
  
## <a name="debuggingerror-checking"></a>调试/错误检查  
  
|Option|用途|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|创建一个文件，其中包含可以轻松报告 bug 的信息。|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|生成调试信息。|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|禁止编译器生成警告的能力。|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|阻止编译器显示与语法相关的错误和警告的代码。|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|禁用整数溢出检查。|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|将警告提升为错误。|  
|`-ruleset:<file>`|指定可禁用特定诊断的规则集文件。|  
  
## <a name="help"></a>Help  
  
|Option|用途|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|显示编译器选项。 此命令等同于指定 `-help` 选项。 未进行编译。|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|显示编译器选项。 此命令等同于指定 `-?` 选项。 未进行编译。|  
  
## <a name="language"></a>语言  
  
|Option|用途|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|指定语言版本：9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|强制执行显式声明变量。|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|执行严格的类语义。|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|指定字符串比较是否应为二进制，或是否应使用特定于区域设置的文本语义。|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|允许在变量声明中使用局部类型推理。|  
  
## <a name="preprocessor"></a>预处理器  
  
|Option|用途|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|定义条件编译的符号。|  
  
## <a name="resources"></a>资源  
  
|Option|用途|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|创建指向托管资源的链接。|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|将托管资源嵌入程序集。|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|将 .ico 文件插入到输出文件。|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|将 Win32 资源插入到输出文件。|  
  
## <a name="miscellaneous"></a>杂项  
  
|Option|用途|  
|---|---|  
|[@（指定响应文件）](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|指定响应文件。|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|指定的 DLL 的基址。|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|指定要用于编译中所有源代码文件的代码页。|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|指定 Visual Basic 编译器应报告内部编译器错误的方式。|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|向 Windows 内核提供下列信息：特定的可执行文件是否支持高熵地址空间布局随机化 (ASLR)。|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|指定包含的类`Sub Main`启动时要使用的过程。|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|不要使用 Vbc.rsp 进行编译|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|导致编译器不引用标准库。|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|指示编译器不在可执行文件中嵌入任何应用程序清单。|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|为输出文件指定编译器面向的处理器平台。|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|搜索要编译的源文件的子目录。|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|指定所有类型声明的命名空间。|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|指定编译器应在不引用 Visual Basic 运行库的情况下进行编译，或在引用特定运行库的情况下进行编译。|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|标识用户定义的 Win32 应用程序清单文件要嵌入到项目的可移植可执行 (PE) 文件。|  
|`-parallel[+&#124;-]`|指定是否使用并发生成 (+)。|  
|`-checksumalgorithm:<alg>`|指定用于计算 PDB 中存储的源文件校验和的算法。  受支持的值为:SHA1（默认值）或 SHA256。|  
  
## <a name="see-also"></a>请参阅

- [按字母顺序列出的 Visual Basic 编译器选项](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)
