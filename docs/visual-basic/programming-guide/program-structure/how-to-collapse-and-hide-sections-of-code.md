---
title: 如何：折叠和隐藏代码 (Visual Basic 中) 的部分
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bf2a7188456097ac227039e4d902a14eb182664c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822255"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>如何：折叠和隐藏代码 (Visual Basic 中) 的部分
`#Region`指令，可折叠并隐藏 Visual Basic 文件中的代码段。 `#Region`指令，可以使用 Visual Studio 代码编辑器时指定的一段代码，你可以展开或折叠。 有选择地隐藏代码的功能使你的文件更易于管理且更易读取。 有关详细信息，请参阅[大纲显示](/visualstudio/ide/outlining)。  
  
 `#Region` 指令支持代码块语义，如`#If...#End If`。 这意味着它们不能在一个块中开始和结束在另一个;开始和结束必须在同一个块中。 `#Region` 在函数中不支持指令。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>若要折叠和隐藏代码节  
  
-   放置之间的代码部分`#Region`和`#End Region`语句，如以下示例所示：  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region`块可以多次使用在代码文件中; 因此，用户可以定义他们自己块的过程和可，反过来，折叠的类。 `#Region` 块也可以嵌套在其他`#Region`块。  
  
    > [!NOTE]
    >  隐藏代码不会阻止从正在编译，并且不影响`#If...#End If`语句。  
  
## <a name="see-also"></a>请参阅

- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region 指令](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [大纲显示](/visualstudio/ide/outlining)
