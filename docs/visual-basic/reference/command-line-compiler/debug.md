---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 9bf7170cee31f92481b15fb1227f21895cd3734d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827973"
---
# <a name="-debug-visual-basic"></a>-调试 (Visual Basic)
使编译器生成调试信息并将其放在输出文件。  
  
## <a name="syntax"></a>语法  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`+` &#124; `-`|可选。 指定`+`或`/debug`会导致编译器生成调试信息并将其放在.pdb 文件中。 指定`-`具有相同的效果完全不指定`/debug`。|  
|`full` &#124; `pdbonly`|可选。 指定编译器生成的调试信息的类型。 如果未指定`/debug:pdbonly`，默认值是`full`，这样您就可以将调试器附加到正在运行的程序。 `pdbonly`参数，允许源代码调试时在调试器中启动程序，但仅在正在运行的程序附加到调试器时才显示汇编语言代码。|  
  
## <a name="remarks"></a>备注  
 使用此选项创建调试版本。 如果未指定`/debug`， `/debug+`，或`/debug:full`，将不能调试程序的输出文件。  
  
 默认情况下，调试信息不会发出 (`/debug-`)。 若要发出调试信息，请指定`/debug`或`/debug+`。  
  
 有关如何配置应用程序的调试性能的信息，请参阅[令映像更易于调试](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
|若要设置的调试 Visual Studio 集成的开发环境中|  
|---|  
|1.在“解决方案资源管理器” 中选择了项目的情况下，在“项目”  菜单上单击“属性” 。 <br />2.单击“编译”选项卡。<br />3.单击“高级编译选项”。<br />4.修改中的值**生成调试信息**框。|  
  
## <a name="example"></a>示例  
 下面的示例将调试信息放入输出文件`App.exe`。  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
