---
title: “<membername>”不能通过 <typename>“<containertype>”在项目外部公开类型“<containertypename>”
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818329"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<成员名称 > 不能公开类型\<类型名称 > 通过在项目外部\<containertype >'\<containertypename >
变量、 过程参数或函数返回公开其容器外，但它被声明为不必须在容器外公开的类型。  
  
 下面的主干代码显示了将生成此错误的情况。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 声明的类型`Protected`， `Friend`， `Protected Friend`，或`Private`用于其声明上下文以外的访问受到限制。 使用与数据，将无法具有受限制更少访问的变量的类型实现此目的。 在上面的主干代码`exposedVar`是`Public`，并将公开`privateClass`不应有权访问它的代码。  
  
 **错误 ID:** BC30909  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   更改访问级别，变量、 过程参数或函数的返回让至少作为其数据类型的访问级别限制性最高。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的访问级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
