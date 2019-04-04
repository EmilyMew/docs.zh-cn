---
title: -目标 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 69312ca3512c5407185df11e66d95ce9f5cdddff
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412287"
---
# <a name="-target-visual-basic"></a>-目标 (Visual Basic)
指定编译器输出的格式。  
  
## <a name="syntax"></a>语法  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>备注  
 下表总结了的效果`-target`选项。  
  
|**选项**|**行为**|  
|----------------|------------------|  
|`-target:exe`|使编译器创建可执行文件的控制台应用程序。<br /><br /> 这是默认选项，如果未`-target`指定选项。 可执行文件创建扩展名为.exe。<br /><br /> 除非另有指定与`/out`选项，输出文件名采用包含输入文件的名称`Sub Main`过程。<br /><br /> 只有一个`Sub Main`过程必需的编译为.exe 文件的源代码文件中。 使用`-main`编译器选项来指定哪些类包含`Sub Main`过程。|  
|`-target:library`|使编译器创建动态链接库 (DLL)。<br /><br /> 动态链接库文件创建具有.dll 扩展名。<br /><br /> 除非另有指定与`-out`选项，输出文件的名称采用第一个输入文件的名称。<br /><br /> 当生成 DLL，`Sub Main`过程不需要。|  
|`-target:module`|使编译器生成的模块，可以添加到程序集。<br /><br /> 输出文件创建一个扩展名为.netmodule。<br /><br /> .NET 公共语言运行时无法加载不具有程序集的文件。 但是，您可以将合并此类文件到程序集清单的程序集使用`-reference`。<br /><br /> 当在一个模块中的代码引用另一个模块中的内部类型时，必须通过使用合并到一个程序集清单这两个模块`-reference`。<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)选项从模块导入元数据。|  
|`-target:winexe`|使编译器创建可执行文件的基于 Windows 的应用程序。<br /><br /> 可执行文件创建扩展名为.exe。 基于 Windows 的应用程序是指提供了从一个用户界面[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]类库或与 Windows Api。<br /><br /> 除非另有指定与`-out`选项，输出文件名采用包含输入文件的名称`Sub Main`过程。<br /><br /> 只有一个`Sub Main`过程必需的编译为.exe 文件的源代码文件中。 你的代码具有多个类具有`Sub Main`过程，请使用`-main`编译器选项来指定哪些类包含`Sub Main`过程|  
|`-target:appcontainerexe`|使编译器创建的可执行基于 Windows 的应用程序必须在应用程序容器中运行。 此设置旨在用于[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]应用程序。<br /><br /> **Appcontainerexe**设置设置了一个位的特征字段中[可移植可执行文件](/windows/desktop/Debug/pe-format)文件。 此位指示必须在应用程序容器中运行该应用。 当设置此位时，如果发生错误`CreateProcess`方法尝试启动外部应用程序容器的应用程序。 除了此位设置， **-target: appcontainerexe**等效于 **-/target: winexe**。<br /><br /> 可执行文件创建扩展名为.exe。<br /><br /> 除非通过使用指定，否则`-out`选项，输出文件名采用包含输入文件的名称`Sub Main`过程。<br /><br /> 只有一个`Sub Main`过程必需的编译为.exe 文件的源代码文件中。 如果你的代码包含多个类具有`Sub Main`过程，请使用`-main`编译器选项来指定哪些类包含`Sub Main`过程|  
|`-target:winmdobj`|使编译器创建的中间文件，则可以将它们转换为 Windows 运行时二进制 (.winmd) 文件。 .Winmd 文件可供 JavaScript 和 c + + 程序，除了托管的语言程序。<br /><br /> 扩展名为.winmdobj 创建中间文件。<br /><br /> 除非另行指定通过使用`-out`选项，输出文件的名称采用第一个输入文件的名称。 一个`Sub Main`过程不是必需的。<br /><br /> .Winmdobj 文件旨在用作输入<xref:Microsoft.Build.Tasks.WinMDExp>导出工具以生成 Windows 元数据 (WinMD) 文件。 WinMD 文件扩展名为.winmd，包含这两个代码从原始库和 WinMD 定义，该 JavaScript、 c + + 和 Windows 运行时使用。|  
  
 除非指定，否则`-target:module`，`-target`导致[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]要添加到输出文件的程序集清单。  
  
 Vbc.exe 的每个实例会生成，最多一个输出文件。 如果指定编译器选项，例如`-out`或`-target`不止一次，编译器进程使生效的最后一个。 有关在编译中的所有文件的信息添加到清单。 除使用创建的文件，所有输出`-target:module`包含在清单中的程序集元数据。 使用[Ildasm.exe （IL 反汇编程序）](../../../framework/tools/ildasm-exe-il-disassembler.md)输出文件中查看元数据。  
  
 `-target` 的缩写形式是 `-t`。  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>若要设置-面向 Visual Studio IDE 中  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。   
  
2.  单击“应用程序”  选项卡。  
  
3.  修改中的值**应用程序类型**框。  
  
## <a name="example"></a>示例  
 下面的代码编译`in.vb`，则创建`in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-参考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET 中的程序集](../../../standard/assembly/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
