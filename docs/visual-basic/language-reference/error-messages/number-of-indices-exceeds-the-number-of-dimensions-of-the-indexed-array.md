---
title: 索引数超过索引数组的维数
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 01659205f271b089fe4e8aa87cf7a8c44e7a4000
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837972"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>索引数超过索引数组的维数
用于访问数组元素的索引数必须完全等同于数组的秩，即为其声明的维数。  
  
 **错误 ID:** BC30106  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   从数组引用中删除下标，直到下标的总数等于数组的秩。 例如：  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a>请参阅

- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
