---
title: 如何：将一个数组赋给另一个数组 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835279"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>如何：将一个数组赋给另一个数组 (Visual Basic)
由于数组是对象，您可以在赋值语句和其他对象类型一样使用它们。 一个数组变量保留一个指向数据构成的数组元素和等级和长度的信息，并分配只复制此指针。  
  
### <a name="to-assign-one-array-to-another-array"></a>若要将一个数组赋给另一个数组  
  
1.  请确保两个数组具有相同的秩 （维数） 和兼容的元素数据类型。  
  
2.  使用标准的赋值语句将源数组赋给目标数组。 不遵循括号数组名。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 当将一个数组赋给另一个时，以下规则适用：  
  
-   **相等的秩。** 目标数组的秩 （维数） 必须是相同的源数组。  
  
     提供两个数组的秩相等，维度不相等。 在分配期间可以更改给定维度中的元素数。  
  
-   **元素类型。** 任一这两个数组必须具有*引用类型*必须具有的元素或这两个数组*值类型*元素。 有关更多信息，请参见 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
    -   如果这两个数组具有值类型的元素，元素数据类型必须完全相同。 唯一的例外是，您可以将分配的数组`Enum`的基类型的数组元素`Enum`。  
  
    -   如果两个数组具有引用类型元素，则必须从目标元素类型派生的源元素类型。 在这种情况下，两个数组具有相同的继承关系作为其元素。 这称为*数组协方差*。  
  
 编译器会报告错误如果违反了上述规则，例如如果数据类型不兼容或者数组的秩不相等。 您可以添加错误处理代码，以确保数组赋值前都兼容。 此外可以使用[TryCast 运算符](../../../../visual-basic/language-reference/operators/trycast-operator.md)关键字，如果你想要避免引发异常。  
  
## <a name="see-also"></a>请参阅

- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum 语句](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [数组转换](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
