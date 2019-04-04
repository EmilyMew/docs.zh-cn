---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 4aca6e9c20dbce7aa8a94067c96fcf44329a6fe4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814869"
---
# <a name="-optionexplicit"></a>-optionexplicit
如果在使用之前未声明变量，会导致编译器报告错误。  
  
## <a name="syntax"></a>语法  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 指定`-optionexplicit+`要求显式声明变量。 `-optionexplicit+`选项是默认值和相同`-optionexplicit`。 `-optionexplicit-`选项启用隐式声明变量。  
  
## <a name="remarks"></a>备注  
 如果源代码文件包含[Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，语句将覆盖`-optionexplicit`命令行编译器设置。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中设置-optionexplicit  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。   
  
2.  单击“编译”选项卡。  
  
3.  修改中的值**Option Explicit**框。  
  
## <a name="example"></a>示例  
 下面的代码编译时`-optionexplicit-`使用。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
