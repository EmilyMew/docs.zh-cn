---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842156"
---
# <a name="-optimize"></a>-optimize
启用或禁用编译器优化。  
  
## <a name="syntax"></a>语法  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`+` &#124; `-`|可选。 `-optimize-`选项会禁用编译器优化。 `-optimize+`选项将启用优化。 默认情况下，禁用优化。|  
  
## <a name="remarks"></a>备注  
 编译器优化会使输出文件更智能、更快并且更有效。 但是，因为优化会导致输出文件中的代码重排`-optimize+`会使调试困难。  
  
 使用生成的所有模块`-target:module`程序集必须使用相同`-optimize`与程序集的设置。 有关详细信息，请参阅[-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。  
  
 你可以组合`-optimize`和`-debug`选项。  
  
|若要设置的优化 Visual Studio 集成的开发环境中|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。<br />     <br />2.单击“编译”选项卡。<br />3.单击“高级”按钮。<br />4.修改**启用优化**复选框。|  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`并启用编译器优化。  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-调试 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
