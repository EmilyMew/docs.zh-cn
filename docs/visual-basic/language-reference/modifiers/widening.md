---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825308"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
指示转换运算符 (`CType`) 将类或结构转换为可以保存原始类或结构的所有可能的值的类型。  
  
## <a name="converting-with-the-widening-keyword"></a>转换使用扩大关键字  
 转换过程都必须指定`Public Shared`除了`Widening`。  
  
 扩大转换在运行时始终成功，并且永远不会导致数据丢失。 示例包括`Single`到`Double`，`Char`到`String`，并为其基类型的派生的类型。 最后一个转换扩大转换，因为所派生的类型包含基类型的所有成员，因此基类型的实例。  
  
 使用代码无需使用`CType`进行扩大转换，即使`Option Strict`是`On`。  
  
 `Widening`关键字可在此上下文中：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 有关示例请参阅的扩大转换和收缩转换运算符定义[如何：定义转换运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="see-also"></a>请参阅

- [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [如何：定义运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [如何：定义转换运算符](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
