---
title: 数组界限不能出现在类型说明符中
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838776"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>数组界限不能出现在类型说明符中
数组大小不能声明为数据类型说明符的一部分。  
  
 **错误 ID:** BC30638  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   指定紧跟变量的名称，而不是数组大小类型之后，如下面的示例中所示的数组的大小。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   定义一个数组并将其与所需的元素数进行初始化，如下面的示例中所示。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>请参阅

- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
