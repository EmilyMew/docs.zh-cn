---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: a1988fcd19c6629d85ae0e739681fd39fe033c0d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843859"
---
# <a name="-vbruntime"></a>-vbruntime
指定编译器应在不引用 Visual Basic 运行库的情况下进行编译，或在引用特定运行库的情况下进行编译。  
  
## <a name="syntax"></a>语法  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>自变量  
 \-  
 编译而无需对 Visual Basic 运行时库的引用。  
  
 \+  
 使用默认的 Visual Basic 运行时库的引用进行编译。  
  
 \*  
 对 Visual Basic 运行时库的引用的情况下编译，嵌入到程序集从 Visual Basic 运行时库的核心功能。  
  
 `path`  
 使用指定的库 (DLL) 的引用进行编译。  
  
## <a name="remarks"></a>备注  
 `-vbruntime`编译器选项可用于指定编译器应编译而无需对 Visual Basic 运行时库的引用。 如果编译而无需对 Visual Basic 运行时库的引用，在代码或语言生成 Visual Basic 运行时帮助器调用的构造记录错误或警告。 (A *Visual Basic 运行时帮助器*是在运行时执行特定的语言语义时调用的 Microsoft.VisualBasic.dll 中定义的函数。)  
  
 `-vbruntime+`选项将生成相同的行为，如果不会发生`-vbruntime`指定开关。 可以使用`-vbruntime+`选项重写之前`-vbruntime`开关。  
  
 大多数对象的`My`使用时，类型将不可用`-vbruntime-`或`-vbruntime:path`选项。  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>嵌入 Visual Basic 运行时的核心功能  
 `-vbruntime*`选项使你能够编译而无需对运行时库的引用。 相反，从 Visual Basic 运行时库的核心功能嵌入用户程序集。 如果你的应用程序在不包含 Visual Basic 运行时的平台上运行，可以使用此选项。  
  
 嵌入以下运行时成员：  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> 类  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> 常量  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 常量  
  
-   某些对象`My`类型  
  
 如果在编译时使用`-vbruntime*`选项和您的代码未使用的核心功能嵌入的 Visual Basic 运行时库中引用的成员，编译器将返回错误，指示该成员不可用。  
  
## <a name="referencing-a-specified-library"></a>引用的指定的库  
 可以使用`path`参数来编译到自定义运行时库而不是默认 Visual Basic 运行时库的引用。  
  
 如果的值为`path`参数为 DLL 的完全限定的路径时，编译器将使用该文件作为运行时库。 如果的值为`path`参数不是 DLL 的完全限定的路径，Visual Basic 编译器将首先搜索当前文件夹中标识的 DLL。 它并将在你通过使用指定的路径中搜索[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)编译器选项。 如果`-sdkpath`未使用编译器选项时，编译器将搜索标识 dll 中的.NET Framework 文件夹 (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`-vbruntime`选项使用对自定义库的引用进行编译。  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 核心 – Visual Studio 2010 SP1 中新的编译模式](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
