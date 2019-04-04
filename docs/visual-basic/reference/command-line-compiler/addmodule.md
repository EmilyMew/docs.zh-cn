---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2de5fe82f1969a2fdb305d45951d7d698252c0c8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816429"
---
# <a name="-addmodule"></a>-addmodule
使编译器让指定文件中的所有类型信息可供当前正在编译的项目使用。  
  
## <a name="syntax"></a>语法  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>自变量  
 `fileList`  
 必需。 以逗号分隔列表，包含元数据，但不是包含程序集清单的文件。 包含空格的文件名应该用引号引起来 ("")。  
  
## <a name="remarks"></a>备注  
 通过列出的文件`fileList`必须与创建参数`-target:module`选项，或使用其他编译器的等效于`-target:module`。  
  
 添加的所有模块`-addmodule`在运行时必须位于与输出文件相同的目录中。 也就是说，可以在编译时，在任何目录中指定模块，但在运行时模块必须在应用程序目录。 如果不存在，则获取<xref:System.TypeLoadException>错误。  
  
 如果指定 （隐式或显式） 任何[-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)选项而`-target:module`与`-addmodule`，将传递到的文件`-addmodule`成为项目的程序集的一部分。 运行具有一个输出文件所需的程序集或更多的文件添加与`-addmodule`。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)包含程序集文件中导入元数据。  
  
> [!NOTE]
>  `-addmodule`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码创建一个模块。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 以下代码导入模块的类型。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 在运行时`t1`，它将输出`802`。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-参考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
