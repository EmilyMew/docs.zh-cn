---
title: 只能根据不带自变量的简单名称或限定名称推断范围变量名称
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 344a813907483dcb0e9f531b54db68a88d77f3dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842377"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能根据不带自变量的简单名称或限定名称推断范围变量名称
在 LINQ 查询中包含一个或多个参数的编程元素。 编译器不能推断该编程元素中的某个范围变量。  
  
 **错误 ID:** BC36599  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  提供的编程元素的显式变量名称，如下面的代码中所示：  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 简介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
