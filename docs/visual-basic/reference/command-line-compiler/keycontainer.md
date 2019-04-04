---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 51cfe4a52af2fbcd51a4f9e2dc738e83fe0852c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839588"
---
# <a name="-keycontainer"></a>-keycontainer
指定密钥对的密钥容器名称从而为程序集赋予强名称。  
  
## <a name="syntax"></a>语法  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`container`|必需。 包含密钥的容器文件。 将文件名括在引号 ("") 如果名称包含空格。|  
  
## <a name="remarks"></a>备注  
 通过将公钥插入到程序集清单，并使用私钥签名最终程序集，编译器创建可共享的组件。 若要生成密钥文件，请在命令行键入 `sn -k file`。 `-i`选项将密钥对安装到容器。 有关详细信息，请参阅[Sn.exe （强名称工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 如果使用编译`-target:module`，保存在模块和合并到编译为程序集时创建的程序集密钥文件的名称[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 还可以将此选项指定为任何 Microsoft 中间语言 (MSIL) 模块的源代码中的自定义特性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。  
  
 此外，可使用 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 将加密信息传递给编译器。 如果需要部分签名的程序集，请使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 请参阅[创建和使用具有强名称程序集](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)有关为程序集签名的详细信息。  
  
> [!NOTE]
>  `-keycontainer`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译源文件`Input.vb`和指定的密钥容器。  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>请参阅

- [.NET 中的程序集](../../../standard/assembly/index.md)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
