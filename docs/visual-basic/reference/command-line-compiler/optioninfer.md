---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 89fcd981dbb5442f6150f539db4c7d404fe8d691
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839842"
---
# <a name="-optioninfer"></a>-optioninfer
允许在变量声明中使用局部类型推理。  
  
## <a name="syntax"></a>语法  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`+` &#124; `-`|可选。 指定 `-optioninfer+` 来启用局部类型推理，或指定 `-optioninfer-` 来阻止它。 没有指定值的 `-optioninfer` 选项等同于 `-optioninfer+`。 不存在 `-optioninfer` 切换时，默认值也是 `-optioninfer+`。 在 Vbc.rsp 响应文件中设置了默认值。|  
  
> [!NOTE]
>  你可使用 `-noconfig` 选项来保留编译器的内部默认值(而非在 vbc.rsp 中指定的那些值）。 此选项默认的编译器是 `-optioninfer-`。  
  
## <a name="remarks"></a>备注  
 如果源代码文件包含[Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)，语句将覆盖`-optioninfer`命令行编译器设置。  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中设置-optioninfer  
  
1.  选择的项目中**解决方案资源管理器**。 在“项目”菜单上，单击“属性”。  
  
2.  上**编译**选项卡上，修改中的值**Option infer**框。  
  
## <a name="example"></a>示例  
 以下代码在启用局部类型推理的情况下编译 `test.vb`。  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [“项目设计器”->“编译”页 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
