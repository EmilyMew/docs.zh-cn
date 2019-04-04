---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 16bfea37a5742ac5aaaabfacdcf03a2b5bedb6db
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819267"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
指示是否是 64 位可执行文件或可执行文件标记[/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)编译器选项支持高熵地址空间布局随机化 (ASLR)。  
  
## <a name="syntax"></a>语法  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 该选项默认处于关闭状态或者您指定`-highentropyva-`。 如果您指定的选项位于`-highentropyva`或`-highentropyva+`。  
  
## <a name="remarks"></a>备注  
 如果指定此选项，Windows 内核的兼容版本可以使用更高程度的熵，内核在 ASLR 随机进程的地址空间布局时。 如果内核使用更高程度的熵，可以向内存区域，例如堆栈或堆分配更多的地址。 因此，猜测特定内存区域的位置会更加困难。  
  
 当选项打开时，目标可执行文件和任何模块上它依赖于它必须是能够处理这些模块作为 64 位进程运行时大于 4 千兆字节 (GB) 的指针值。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
