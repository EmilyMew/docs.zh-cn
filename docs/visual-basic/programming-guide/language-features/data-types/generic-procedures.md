---
title: Generic Procedures in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 4aed16ce9eb59da54156a0cd5f1594819788521b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818912"
---
# <a name="generic-procedures-in-visual-basic"></a>Generic Procedures in Visual Basic
一个*泛型过程*，也称为*泛型方法*，是使用至少一个类型参数定义的过程。 这使得调用代码来定制其要求的数据类型的每次调用该过程。  
  
 过程是不是简单地由于正在定义在泛型类或泛型结构。 若要为泛型，该过程必须采用至少一个类型参数，除了可能需要的所有普通参数。 泛型类或结构可以包含非泛型过程和非泛型类、 结构或模块可以包含泛型过程。  
  
 泛型过程可以在其正常参数列表中，其返回类型，如果它有一个，并在其过程代码中使用其类型参数。  
  
## <a name="type-inference"></a>类型推断  
 未提供任何类型参数在所有情况下，可以调用泛型过程。 如果您以这种方式，编译器将尝试确定要传递给过程的类型参数的相应的数据类型。 这称为*类型推理*。 下面的代码演示如何调用中，编译器推断它应将类型传递`String`对该类型参数`t`。  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 如果编译器无法推断调用上下文的类型参数，则将报告错误。 此类错误的一个可能原因是数组秩不匹配。 例如，假设您定义普通参数作为数组的类型参数。 如果调用的泛型过程提供不同的秩 （维数），数组不匹配会导致类型推理失败。 下面的代码演示如何调用中的二维数组传递给过程所需的一维数组。  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 可以仅通过省略的所有类型参数调用类型推理。 如果您提供一个类型实参，则必须提供所有这些。  
  
 仅对泛型过程支持的类型推理。 不能调用上泛型类、 结构、 接口或委托的类型推理。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例定义了一个泛型`Function`过程，用于在数组中查找特定元素。 它定义一个类型参数，并使用它来构建在参数列表中的两个参数。  
  
### <a name="code"></a>代码  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>注释  
 前面的示例要求进行比较的能力`searchValue`针对每个元素的`searchArray`。 若要确保此功能，它可以约束类型参数`T`实现<xref:System.IComparable%601>接口。 该代码使用<xref:System.IComparable%601.CompareTo%2A>方法而不是`=`运算符，因为没有为提供的类型参数不能保证`T`支持`=`运算符。  
  
 你可以测试`findElement`用下面的代码的过程。  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 上述调用`MsgBox`分别显示"0"、"1"和"-1"。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的泛型类型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [如何：定义可对不同数据类型提供相同功能的类](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [如何：使用泛型类](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [过程](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [过程参数和自变量](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [类型列表](../../../../visual-basic/language-reference/statements/type-list.md)
- [参数列表](../../../../visual-basic/language-reference/statements/parameter-list.md)
