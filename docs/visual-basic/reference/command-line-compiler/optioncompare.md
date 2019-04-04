---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 0c23a74f91cd6666a0c4bef5ea67c58430c511b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819398"
---
# <a name="-optioncompare"></a>-optioncompare
指定如何进行字符串比较。  
  
## <a name="syntax"></a>语法  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>备注  
 您可以指定`-optioncompare`在两种形式之一：`-optioncompare:binary`使用二进制字符串比较和`-optioncompare:text`使用文本字符串比较。 默认情况下，编译器使用`-optioncompare:binary`。  
  
 在 Microsoft Windows 中的当前代码页确定二进制排序顺序。 典型的二进制排序顺序是按如下所示：  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 基于文本的字符串比较将基于由您的系统区域设置的不区分大小写的文本排序顺序。 典型的文本排序顺序是按如下所示：  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中设置-optioncompare  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。   
  
2.  单击“编译”选项卡。  
  
3.  修改中的值**Option Compare**框。  
  
### <a name="to-set--optioncompare-programmatically"></a>若要以编程方式设置-optioncompare  
  
-   请参阅[Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="example"></a>示例  
 下面的代码编译`ProjFile.vb`，并使用二进制字符串比较。  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [“选项”对话框 ->“项目”->“Visual Basic 默认值”](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
