---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: d1676cea520c42a40082e31cce9de9797b06e9ee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814037"
---
# <a name="-main"></a>-main
指定包含 `Sub Main` 过程的类或模块。  
  
## <a name="syntax"></a>语法  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>自变量  
 `location`  
 必需。 包含模块的类的名称`Sub Main`在程序启动时要调用的过程。 这可能是在窗体 **-主： module**或 **-main:namespace.module**。  
  
## <a name="remarks"></a>备注  
 创建可执行文件或 Windows 可执行程序时，请使用此选项。 如果 **-主**省略选项，编译器将搜索有效的共享`Sub Main`所有公共类和模块中。  
  
 请参阅[在 Visual Basic 中的 Main 过程](../../../visual-basic/programming-guide/program-structure/main-procedure.md)有关的各种形式的讨论`Main`过程。  
  
 当`location`是一个类，继承自<xref:System.Windows.Forms.Form>，则编译器会提供默认值`Main`如果类没有启动的应用程序的过程`Main`过程。 这样可以在命令行在开发环境中创建的代码编译。  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>若要设置的主 Visual Studio 集成的开发环境中  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。  
  
2.  单击“应用程序”  选项卡。  
  
3.  请确保**启用应用程序框架**未选中复选框。  
  
4.  修改中的值**启动对象**框。  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`并`T3.vb`，并指定该`Sub Main`过程将在中找到`Test2`类。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [在 Visual Basic 中的主要过程](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
