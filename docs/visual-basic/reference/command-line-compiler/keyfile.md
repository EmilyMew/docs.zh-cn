---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833295"
---
# <a name="-keyfile"></a>-keyfile
指定包含密钥或密钥对的文件从而为程序集赋予强名称。  
  
## <a name="syntax"></a>语法  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>自变量  
 `file`  
 必需。 包含密钥的文件。 如果文件名包含空格，将名称括在引号 ("")。  
  
## <a name="remarks"></a>备注  
 编译器将公钥插入到程序集清单，并使用私钥对进行签名最终程序集。 若要生成密钥文件，请在命令行键入 `sn -k file`。 有关详细信息，请参阅[Sn.exe （强名称工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 如果使用编译`-target:module`，保存在模块和合并到编译为程序集时创建的程序集密钥文件的名称[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 也可以使用 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 将加密信息传递给编译器。 如果需要部分签名的程序集，请使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 此外可以指定此选项的自定义特性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 为 Microsoft 中间语言的任何模块的源代码中。  
  
 两者`-keyfile`并[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) （通过命令行选项或通过自定义特性） 中指定在同一编译中，编译器将首先尝试密钥容器。 如果成功，则使用密钥容器中的信息对程序集签名。 如果编译器没有找到密钥容器，它将尝试用指定的文件`-keyfile`。 如果此操作成功、 使用密钥文件中的信息签名程序集和密钥信息安装到密钥容器中 (类似于`sn -i`)，以便下一次编译中，密钥容器将有效。  
  
 请注意，密钥文件可能仅包含公钥。  
  
 请参阅[创建和使用具有强名称程序集](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)有关为程序集签名的详细信息。  
  
> [!NOTE]
>  `-keyfile`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译源文件`Input.vb`，并指定密钥文件。  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>请参阅

- [.NET 中的程序集](../../../standard/assembly/index.md)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-参考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
