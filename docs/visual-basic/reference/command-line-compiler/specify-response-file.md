---
title: '@（指定响应文件）(Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838113"
---
# <a name="-specify-response-file-visual-basic"></a>@（指定响应文件）(Visual Basic)
指定包含编译器选项的文件和要编译的源代码文件。  
  
## <a name="syntax"></a>语法  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>自变量  
 `response_file`  
 必需。 列出编译器选项或要编译的源代码文件的文件。 将文件名括在引号 ("") 如果包含空格。  
  
## <a name="remarks"></a>备注  
 编译器处理编译器选项和源代码文件的响应文件中指定，如同它们已在命令行上指定的一样。  
  
 若要指定多个响应文件在编译时，指定多个响应文件选项，如下所示。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 在响应中文件、 多个编译器选项和源代码文件可以出现在同一行中。 单个编译器选项规范必须出现在同一行中 （不能跨多个行）。 响应文件可以具有开头的注释`#`符号。  
  
 你可以组合使用一个或多个响应文件中指定的选项在命令行上指定的选项。 编译器遇到它们处理命令选项。 因此，命令行参数可以覆盖先前列出的选项响应文件中。 相反，响应文件中的选项重写先前在命令行上或其他响应文件中列出的选项。  
  
 Visual Basic 提供 Vbc.rsp 文件，位于 Vbc.exe 文件所在的同一目录中。 默认情况下包含 Vbc.rsp 文件，除非`-noconfig`使用选项。 有关详细信息，请参阅[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。  
  
> [!NOTE]
>  `@`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的行是从示例响应文件。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`@`具有名为的响应文件选项`File1.rsp`。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
