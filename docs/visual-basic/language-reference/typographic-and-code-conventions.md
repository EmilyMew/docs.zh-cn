---
title: 版式和代码约定 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 3255dff8268cd5500a1244716f37bf30f5b43cfb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828623"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>版式和代码约定 (Visual Basic)
Visual Basic 文档中使用以下版式和代码约定。  
  
## <a name="typographic-conventions"></a>排字约定  
  
|示例|描述|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|特定于语言的关键字和运行时成员的首字母大写，其格式，在此示例中所示。|  
|**SmallProject**， **ButtonCollection**|单词和短语指示您键入的格式如在此示例中所示。|  
|[Module 语句](../../visual-basic/language-reference/statements/module-statement.md)|在此示例中所示，可以单击以转到另一个帮助页的链接的格式。|  
|*object*, *variableName*, `argumentList`|您提供的信息的占位符的格式，在此示例中所示。|  
|[阴影] [ *expressionList* ]|在语法中，可选项括在括号中。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|在语法中，必须进行两个或多个项之间进行选择时，物料被括在大括号中并由竖线分隔。<br /><br /> 您必须选择一个，且只有一个项。|  
|[ `Protected` &#124; `Friend` ]|在语法中时您可以选择两个或多个项之间的, 项是用方括号括起来并由竖线分隔。<br /><br /> 可以选择的项的任意组合或任何项。|  
|[{ `ByVal` &#124; `ByRef` }]|在语法中，您可以选择多个项，但也可以完全省略这些项时项括在方括号括在大括号和由竖线分隔。|  
|*memberName*1， *memberName*2， *memberName*3|在示例中所示，按下标，进行区分同一占位符的多个实例。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|在语法中，省略号 （...） 用于指示立即前面省略号类型的项目数量不确定。<br /><br /> 在代码中，省略号表示为了清楚起见而省略的代码。|  
|ESC 键，输入|密钥名称和键盘上的按键顺序出现在全部以大写字母。|  
|ALT+F1|密钥名称之间出现的加号 （+），您必须同时按下另按住一个键。 例如，ALT + F1 表示按下 F1 键时按住 ALT 键。|  
  
## <a name="code-conventions"></a>代码约定  
  
|示例|描述|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|代码示例显示在固定间距字体，并在此示例中所示的格式。|  
|上一语句设置的值`sampleString`到"Hello，world ！"|在此示例中所示，解释性文本中的代码元素出现在固定间距字体。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|代码注释被引入的撇号 （'） 或 REM 关键字。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|空格和下划线 (_) 行尾指示该语句将继续在下一行。|  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 语言参考](../../visual-basic/language-reference/index.md)
- [关键字](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 运行库成员](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic 命名约定](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [如何：在代码中拆分和合并语句](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [代码中的注释](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
