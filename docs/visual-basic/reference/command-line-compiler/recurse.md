---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816416"
---
# <a name="-recurse"></a>-recurse
编译源代码文件中指定的目录或项目目录的所有子目录。  
  
## <a name="syntax"></a>语法  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>自变量  
 `dir`  
 可选。 希望从中开始搜索的目录。 如果未指定，在项目目录中开始搜索。  
  
 `file`  
 必需。 要搜索的文件。 允许通配符。  
  
## <a name="remarks"></a>备注  
 可以在文件名中使用通配符来编译项目目录中的所有匹配文件无需使用`-recurse`。 如果不指定任何输出文件的名称，编译器将基于处理的第一个输入文件上的输出文件名称。 这通常是在编译时按字母顺序查看的文件列表中的第一个文件。 出于此原因，最好指定输出文件使用`-out`选项。  
  
> [!NOTE]
>  `-recurse`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的命令编译当前目录中的所有 Visual Basic 文件。  
  
```console
vbc *.vb  
```  
  
 下面的命令编译中的所有 Visual Basic 文件`Test\ABC`directory 和任何目录，然后生成`Test.ABC.dll`。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
