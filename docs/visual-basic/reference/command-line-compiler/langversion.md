---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839713"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
使编译器接受仅包含指定版本的 Visual Basic 语言的语法。  
  
## <a name="syntax"></a>语法  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>自变量  
 `version`  
 必需。 要在编译期间使用的语言版本。 接受的值是`9`， `10`， `11`， `12`， `14`， `15`， `15.3`， `15.5`，`default`和`latest`。

 任何整数还可以指定使用`.0`次要版本，例如，作为`11.0`。

 您可以看到所有可能值的列表，通过指定`-langversion:?`命令行上。  
  
## <a name="remarks"></a>备注  
 `-langversion`选项指定编译器接受何种语法。 例如，如果你指定的语言版本为 9.0，编译器将生成有效仅在版本 10.0 及更高版本的语法的错误。  
  
 开发面向不同版本的.NET Framework 的应用程序时，可以使用此选项。 例如，如果面向.NET Framework 3.5，可以使用此选项以确保不使用从语言版本 10.0 的语法。  
  
 可以设置`-langversion`直接只能通过使用命令行。 有关详细信息，请参阅[面向特定的 .NET Framework 版本](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)。  
  
## <a name="example"></a>示例  
 下面的代码编译`sample.vb`为 Visual Basic 9.0。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [面向特定的 .NET Framework 版本](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
