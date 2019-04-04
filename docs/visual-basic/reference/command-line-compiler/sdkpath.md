---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 2024ccadb06fdea0c24d9d304c2fe040f8cce1d5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814317"
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## <a name="syntax"></a>语法  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>自变量  
 `path`  
 包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 用于编译的版本的目录。 它才不验证此路径。 将目录名称括在引号 ("") 如果包含空格。  
  
## <a name="remarks"></a>备注  
 此选项会告知 Visual Basic 编译器从非默认位置加载的 mscorlib.dll 和 Microsoft.VisualBasic.dll 文件。 `-sdkpath`选项旨在用于[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。 [!INCLUDE[Compact](~/includes/compact-md.md)]使用不同版本的这些支持库，以避免使用类型和语言功能的设备上找不到。  
  
> [!NOTE]
>  `-sdkpath`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。 `-sdkpath`加载 Visual Basic 设备项目时，设置选项。  
  
 您可以指定通过使用编译器应编译而无需对 Visual Basic 运行时库的引用`-vbruntime`编译器选项。 有关详细信息，请参阅[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## <a name="example"></a>示例  
 下面的代码编译`Myfile.vb`与[!INCLUDE[Compact](~/includes/compact-md.md)]，使用版本的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的默认安装目录中找到[!INCLUDE[Compact](~/includes/compact-md.md)]C 驱动器上。 通常情况下，将使用最新版本的[!INCLUDE[Compact](~/includes/compact-md.md)]。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
