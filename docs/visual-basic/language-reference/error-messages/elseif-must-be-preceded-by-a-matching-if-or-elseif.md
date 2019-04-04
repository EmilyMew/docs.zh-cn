---
title: “#ElseIf”前面必须是匹配的“#If”或“#ElseIf”
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: fbb8ce974a618349bd4b5e7a2a25a165d91787a7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832250"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>“#ElseIf”前面必须是匹配的“#If”或“#ElseIf”
`#ElseIf` 是条件编译指令。 `#ElseIf`子句的前面必须是匹配`#If`或`#ElseIf`子句。  
  
 **错误 ID:** BC30014  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查前面`#If`或`#ElseIf`不从该分离`#ElseIf`插入的条件编译块或放置有误`#End If`。  
  
2.  如果`#ElseIf`的前面有`#Else`指令，请移除`#Else`或将其更改为`#ElseIf`。  
  
3.  如果其他一切正常，请将 `#If` 指令添加到条件编译块的开头。  
  
## <a name="see-also"></a>请参阅

- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
