---
title: 此数组被固定或临时锁定 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f0b80e2be007ff44569365f37a2331f1ecd7a216
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839400"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>此数组被固定或临时锁定 (Visual Basic)
此错误具有以下可能的原因：  
  
-   使用`ReDim`若要更改的固定大小数组的元素数。  
  
-   Redimensioning 模块级别动态数组，其中的一个元素具有作为参数传递给过程。 如果传递一个元素，则数组将被锁定以防止取消分配内存的过程中的引用参数。  
  
-   尝试将一个值赋给`Variant`变量包含一个数组，但`Variant`当前被锁定。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  将原始数组而不是通过声明它具有固定动态`ReDim`（如果声明数组过程中），或通过声明而无需指定的元素数 （如果在模块级别声明数组。  
  
2.  确定是否真的需要传递了元素，因为它是在模块中的所有过程中可见。  
  
3.  确定锁定`Variant`并更正它。  
  
## <a name="see-also"></a>请参阅

- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
