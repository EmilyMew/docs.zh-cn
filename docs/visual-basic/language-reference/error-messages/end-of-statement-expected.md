---
title: 需要语句结束
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: ab6a4a0e6736e2af9c1fa0dd170b6aa4c42d9e4a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817144"
---
# <a name="end-of-statement-expected"></a>需要语句结束
该语句是语法上完成，但其他编程元素如下所示完成该语句的元素。 需要在每个语句末尾行结束符。
  
 行终止符将 Visual Basic 源文件字符划分为行。 行终止符的示例包括 Unicode 回车符返回字符 （HD），Unicode 换行字符 (HA），并使用 Unicode 回车字符后跟 Unicode 换行字符。 有关行终止符的详细信息，请参阅[Visual Basic 语言规范](~/_vblang/spec/lexical-grammar.md#line-terminators)。
  
 **错误 ID:** BC30205
  
## <a name="to-correct-this-error"></a>更正此错误
  
1.  检查以确定是否两个不同的语句无意中已放在同一行。
  
2.  完成该语句的元素之后插入一个行结束符。
  
## <a name="see-also"></a>请参阅

- [如何：在代码中拆分和合并语句](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
