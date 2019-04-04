---
title: 类型参数不能用作限定符
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 974d2935e64151109b688f576229fb008b59b229
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819796"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>类型参数不能用作限定符
编程元素限定包含类型参数的限定字符串中。  
  
 类型参数表示构造泛型类型时将提供的类型的要求。 它不表示特定的已定义的类型。 限定字符串必须包含在编译时定义的元素。  
  
 以下语句可能会生成此错误。  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **错误 ID:** BC32098  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  从限定字符串中删除类型参数或替换已定义的类型。  
  
2.  如果您需要使用一个构造的类型来查找正在限定的编程元素，则必须使用其他程序逻辑。  
  
## <a name="see-also"></a>请参阅

- [对已声明元素的引用](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的泛型类型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [类型列表](../../../visual-basic/language-reference/statements/type-list.md)
