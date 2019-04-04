---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 7b9485c1bc2f87ca9f007a4e1ce2f63c055100c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815974"
---
# <a name="-netcf"></a>-netcf
设置编译器从而以 [!INCLUDE[Compact](~/includes/compact-md.md)] 为目标。  
  
## <a name="syntax"></a>语法  
  
```  
-netcf  
```  
  
## <a name="remarks"></a>备注  
 `-netcf`选项将导致目标到 Visual Basic 编译器[!INCLUDE[Compact](~/includes/compact-md.md)]而不是完整[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 仅存在于完整的语言功能[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]被禁用。  
  
 `-netcf`选项旨在用于[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)。 通过禁用的语言功能`-netcf`是相同的语言功能与所针对的文件中不存在`-sdkpath`。  
  
> [!NOTE]
>  `-netcf`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。 `-netcf`加载 Visual Basic 设备项目时，设置选项。  
  
 `-netcf`选项可更改以下语言功能：  
  
-   [最终\<关键字 > 语句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)关键字，这将终止执行程序，已禁用。 以下程序编译和运行而无需`-netcf`但在编译时会失败`-netcf`。  
  
     [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]  
  
-   后期绑定，在所有表单中，已禁用。 当遇到已识别的后期绑定方案时，会生成编译时错误。 以下程序编译和运行而无需`-netcf`但在编译时会失败`-netcf`。  
  
     [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]  
  
-   [自动](../../../visual-basic/language-reference/modifiers/auto.md)， [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)，并[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修饰符处于禁用状态。 语法[Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)语句也被修改为`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。 下面的代码演示的效果`-netcf`上一次编译。  
  
     [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]  
  
-   使用已从 Visual Basic 的 Visual Basic 6.0 关键字生成不同的错误时`-netcf`使用。 这会影响以下关键字的错误消息：  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>示例  
 下面的代码编译`Myfile.vb`与[!INCLUDE[Compact](~/includes/compact-md.md)]，使用版本的 mscorlib.dll 和 Microsoft.VisualBasic.dll 的默认安装目录中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 驱动器上。 通常情况下，将使用最新版本的[!INCLUDE[Compact](~/includes/compact-md.md)]。  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
