---
title: 数组转换 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 88002e2c099ed9503beddb190d243aadcc1087fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830196"
---
# <a name="array-conversions-visual-basic"></a>数组转换 (Visual Basic)
可以将数组类型转换为另一个数组类型，但必须满足以下条件：  
  
-   **秩相等。** 两个数组的秩必须相同，即，它们必须具有相同数量的维度。 但是，不需要的相应维度的长度相同。  
  
-   **元素数据类型。** 这两个数组的元素的数据类型必须是引用类型。 你不能转换`Integer`到数组`Long`数组，或者甚至到`Object`，因为涉及至少一个值类型数组。 有关更多信息，请参见 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
-   **支持。** 扩大或收缩转换时，必须是两个数组的元素类型之间可能的。 符合此要求的一个示例是之间尝试执行的转换`String`数组和数组的类派生自<xref:System.Attribute?displayProperty=nameWithType>。 这两种类型迥然不同，并且它们之间不存在任何类型的转换。  
  
 一个数组类型转换为另一个是扩大转换或收缩具体取决于是否扩大或收缩的相应元素的转换。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="conversion-to-an-object-array"></a>转换为对象数组  
 当你声明`Object`而无需初始化它，其元素类型的数组是`Object`，只要它保持未初始化。 当将其设置为特定类的数组时，它将采用该类的类型。 但是，其基础类型仍是`Object`，随后可以将其设置为一个不相关的类的另一个数组。 由于所有类都派生自`Object`，可以从任何类更改数组的元素类型，与其他任何类。  
  
 在以下示例中，不存在转换类型之间`student`并`String`，但同时派生`Object`，因此，所有分配都都有效。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>数组的基础类型。  
 如果您最初声明具有特定类的数组，其基础的元素类型是该类。 如果您随后将其设置到另一个类的一个数组，必须有两个类之间的转换。  
  
 在以下示例中，`students`是`student`数组。 由于不存在转换之间`String`和`student`，最后一个语句将失败。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [隐式转换和显式转换](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字符串和其他类型之间的转换](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：将对象转换为 Visual Basic 中的另一种类型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
