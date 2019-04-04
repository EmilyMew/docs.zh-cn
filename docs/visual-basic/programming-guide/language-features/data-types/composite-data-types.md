---
title: 复合数据类型 (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833810"
---
# <a name="composite-data-types-visual-basic"></a>复合数据类型 (Visual Basic)
除了基本数据类型 Visual Basic 提供，您可以汇集不同类型创建的项*复合数据类型*如结构、 数组和类。 从基本类型和其他复合类型，您可以构建复合数据类型。 例如，可以使用数组成员定义结构元素的数组或结构。  
  
## <a name="data-types"></a>数据类型  
 复合类型是不同于其任意组件的数据类型。 例如，数组`Integer`元素的不是`Integer`数据类型。  
  
 通常情况下根据需要使用元素类型、 括号和逗号表示数组数据类型。 例如的一维数组`String`元素表示为`String()`，和的二维数组`Boolean`元素表示为`Boolean(,)`。  
  
## <a name="structure-types"></a>结构类型  
 没有一种数据类型包含所有结构。 相反，每个定义的结构表示唯一的数据类型，即使两个结构的相同顺序定义相同的元素。 但是，如果创建具有相同结构的两个或多个实例时，Visual Basic 将认为它们是相同的数据类型。  
  
## <a name="tuples"></a>元组

元组是包含两个或多个字段的类型预定义的轻型结构。 从 Visual Basic 2017 开始支持元组。 元组通常用于从单个方法调用返回多个值，而无需按引用传递参数或打包更粗线的类或结构中返回的字段。 请参阅[元组](tuples.md)元组的详细信息的主题。

## <a name="array-types"></a>数组类型  
 没有一种数据类型包含所有数组。 通过以下方法确定数组的特定实例的数据类型：  
  
-   这一事实的一个数组  
  
-   数组的秩 （维数）  
  
-   数组的元素类型  
  
 具体而言，给定维度的长度不是实例的数据类型的一部分。 下面的示例阐释了这一点。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 在前面的示例中，数组变量`arrayA`并`arrayB`被视为是相同的数据类型 — `Byte()` — 即使它们初始化为不同的长度。 变量`arrayB`和`arrayC`不属于同一类型，因为它们的元素类型不同。 变量`arrayC`和`arrayD`不属于同一类型，因为它们的秩不同。 变量`arrayD`并`arrayE`具有相同的类型 — `Short(,)` — 因为它们的秩和元素类型是相同的即使`arrayD`尚未初始化。  
  
 在数组上的详细信息，请参阅[数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="class-types"></a>类类型  
 没有一种数据类型组成的所有类。 尽管一个类可以继承自另一个类，每个是单独的数据类型。 同一个类的多个实例是相同的数据类型。 如果将一个类实例变量分配到另一个，不仅它们具有相同的数据类型，它们指向内存中的同一个类实例。  
  
 类的详细信息，请参阅[对象和类](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Visual Basic 中的泛型类型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [值类型和引用类型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：在一个变量中保留多个值](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
