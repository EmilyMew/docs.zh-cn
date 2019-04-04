---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: f6d896fb0d41a8fa3ed613d29bc3fca2bd14cc5e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832784"
---
# <a name="-verbose"></a>-verbose
会导致编译器生成详细的状态和错误消息。  
  
## <a name="syntax"></a>语法  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 指定`-verbose`相当于将指定`-verbose+`，这将导致编译器发出详细消息。 此选项的默认值是`-verbose-`。  
  
## <a name="remarks"></a>备注  
 `-verbose`选项显示有关由编译器发出的错误总数信息、 报告的程序集加载的模块，并显示当前正在编译的文件。  
  
> [!NOTE]
>  `-verbose`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译`In.vb`并指示编译器以显示详细的状态信息。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
