---
title: 溢出（Visual Basic 运行时错误）
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 47e9106b7355db6ae02ee263dbea82d41a69ed5e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816975"
---
# <a name="overflow-visual-basic-run-time-error"></a>溢出（Visual Basic 运行时错误）
当你尝试赋值超出分配的目标的限制时，将导致溢出。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  请确保分配、 计算和数据类型的转换不是太大而无法表示允许的值，该类型的变量的范围内，并将值分配给类型的变量的结果可以容纳更大的值范围如有必要。  
  
2.  请确保对属性分配符合它们所做的属性的范围。  
  
3.  请确保在强制转换为整数的计算中使用的数字不具有大于整数的结果。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [错误类型](../../../visual-basic/programming-guide/language-features/error-types.md)
