---
title: 嵌套函数没有与委托“<delegatename>”兼容的签名。
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 04eae6d2c6d64e8a0f46ae3c2801a7eb6d893dca
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822253"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>嵌套的函数没有与委托兼容的签名\<委托名 >'
Lambda 表达式已分配到具有兼容签名的委托。 例如，在下面的代码中，委托`Del`具有两个整数参数。  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 如果具有一个自变量的 lambda 表达式声明为类型会引发错误`Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **错误 ID:** BC36532  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   调整委托定义或分配的 lambda 表达式，以便签名是兼容。  
  
## <a name="see-also"></a>请参阅

- [宽松委托转换](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
