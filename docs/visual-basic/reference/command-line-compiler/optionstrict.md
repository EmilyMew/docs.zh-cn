---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 5479c312ae7eb7a166803a6e1238806aae9bd656
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835656"
---
# <a name="-optionstrict"></a>-optionstrict
强制执行严格类型语义来限制隐式类型转换。  
  
## <a name="syntax"></a>语法  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 `-optionstrict+`选项将限制隐式类型转换。 此选项的默认值是`-optionstrict-`。 `-optionstrict+`选项等同于`-optionstrict`。 可以使用同时用于许可类型语义。  
  
 `custom`  
 必需。 当未遵从严格语言语义时发出警告。  
  
## <a name="remarks"></a>备注  
 当`-optionstrict+`有效时，是可以隐式进行唯一扩大类型转换。 隐式收缩类型转换，例如分配`Decimal`键入指向整数的类型对象的对象，将报告为错误。  
  
 若要生成的隐式收缩类型转换警告，请使用`-optionstrict:custom`。 使用`-nowarn:numberlist`忽略特定警告和`-warnaserror:numberlist`将特定警告视为错误。  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中设置-optionstrict  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 上**项目**菜单上，单击**属性。**   
  
2.  单击“编译”选项卡。  
  
3.  修改中的值**Option Strict**框。  
  
### <a name="to-set--optionstrict-programmatically"></a>若要以编程方式设置-optionstrict  
  
-   请参阅[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="example"></a>示例  
 下面的代码编译`Test.vb`使用严格类型语义。  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
