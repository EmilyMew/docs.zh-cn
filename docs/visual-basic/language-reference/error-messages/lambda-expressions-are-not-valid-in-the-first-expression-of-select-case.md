---
title: Lambda 表达式在“Select Case”语句的第一个表达式中无效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e51ba4ad0910d0db2b927f84303e5c55515f4b84
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843444"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Lambda 表达式在“Select Case”语句的第一个表达式中无效
不能使用 lambda 表达式中的测试表达式`Select Case`语句。 返回的函数，测试表达式的 lambda 表达式定义`Select Case`语句必须是基本数据类型。  
  
 下面的代码会导致此错误：  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **错误 ID:** BC36635  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   检查你的代码以确定是否可以使用其他条件构造，例如 `If...Then...Else` 语句。  
  
-   您可能打算调用该函数，如下面的代码中所示：  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>请参阅

- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)
