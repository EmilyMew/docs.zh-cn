---
title: “<membername>”在继承接口“<interfacename1>”和“<interfacename2>”之间不明确
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 4415608bcfca63b43b3d9ebf17ce622ccd418775
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820832"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>'\<成员名称 > 之间的继承接口的不明确\<interfacename1 > 和\<interfacename2 >
接口从多个接口继承具有相同名称的两个或多个成员。  
  
 **错误 ID:** BC30685  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   将值转换为你想要使用; 的基接口例如：  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>请参阅

- [接口](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
