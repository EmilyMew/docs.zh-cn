---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816650"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
指定过程参数采用一个可选的指定类型的元素的数组。 `ParamArray` 可以使用仅在参数列表的最后一个参数上。  
  
## <a name="remarks"></a>备注  
 `ParamArray` 可以将任意数量的参数传递给该过程。 一个`ParamArray`始终使用声明参数[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。  
  
 您可以提供一个或多个参数`ParamArray`通过传递相应的数据数组的参数类型，则一列以逗号分隔的值或执行任何操作根本。 详细信息，请参阅"调用 ParamArray"中[参数数组](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
> [!IMPORTANT]
>  每当处理数组可以是无限期较大，则存在无限大的某种内部容量的应用程序的风险。 如果接受从调用代码的参数数组，应测试它的长度，并采取相应措施，如果你的应用程序太大。  
  
 `ParamArray` 修饰符可用于下面的上下文中：  
  
 [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>请参阅

- [关键字](../../../visual-basic/language-reference/keywords/index.md)
- [参数数组](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
