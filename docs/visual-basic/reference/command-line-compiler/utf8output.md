---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833624"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
显示使用 UTF-8 编码的编译器输出。  
  
## <a name="syntax"></a>语法  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 此选项的默认值是`-utf8output-`，这意味着编译器输出不会使用 utf-8 编码。 指定 `-utf8output` 与指定 `-utf8output+` 相同。  
  
## <a name="remarks"></a>备注  
 在某些国际配置中，编译器输出无法在控制台中正确显示。 在这种情况下，使用`-utf8output`和编译器输出重定向到一个文件。  
  
> [!NOTE]
>  `-utf8output`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译`In.vb`并指示编译器显示输出使用 utf-8 编码。  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
