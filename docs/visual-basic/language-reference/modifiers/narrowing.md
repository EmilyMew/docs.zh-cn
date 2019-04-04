---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838841"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
指示转换运算符 (`CType`) 将类或结构转换为可能无法保存某些原始类或结构的可能值的类型。  
  
## <a name="converting-with-the-narrowing-keyword"></a>转换与收缩关键字  
 转换过程都必须指定`Public Shared`除了`Narrowing`。  
  
 收缩转换执行不总是在运行时，成功和可以故障或会导致数据丢失。 示例包括`Long`到`Integer`，`String`到`Date`，并为派生类型的基类型。 最后一个转换收缩转换，因为基类型可能不包含派生类型的所有成员，因此不是派生类型的实例。  
  
 如果`Option Strict`是`On`，则使用代码必须使用`CType`收缩的所有转换。  
  
 `Narrowing`关键字可在此上下文中：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>请参阅

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定义运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
