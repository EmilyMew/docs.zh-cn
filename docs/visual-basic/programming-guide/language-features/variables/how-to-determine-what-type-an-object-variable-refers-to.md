---
title: 如何：确定哪种类型的对象变量引用 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: dc6f54719d4f30be00b7b85f0ab18c4cb02b0d7c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816403"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>如何：确定哪种类型的对象变量引用 (Visual Basic)
对象变量包含指向其他位置所存储的数据的指针。 在运行时可以更改该数据的类型。 在任何时刻，您可以使用<xref:System.Type.GetTypeCode%2A>方法，以确定当前的运行时类型，或[TypeOf 运算符](../../../../visual-basic/language-reference/operators/typeof-operator.md)要找出当前运行时类型是否与指定的类型兼容。  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>若要确定的精确类型的对象变量当前引用  
  
1.  对象变量上调用<xref:System.Object.GetType%2A>方法来检索<xref:System.Type?displayProperty=nameWithType>对象。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  上<xref:System.Type?displayProperty=nameWithType>类中，调用共享的方法<xref:System.Type.GetTypeCode%2A>检索<xref:System.TypeCode>对象的类型的枚举值。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     你可以测试<xref:System.TypeCode>枚举值与任何枚举成员如感兴趣， `Double`。  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>若要确定对象变量的类型与指定类型兼容  
  
-   使用`TypeOf`运算符配合[Is 运算符](../../../../visual-basic/language-reference/operators/is-operator.md)若要测试与对象`TypeOf`...`Is`表达式。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`...`Is`表达式返回`True`对象的运行时类型是否与指定的类型兼容。  
  
     兼容性的条件取决于指定的类型是类、 结构或接口。 一般情况下，类型兼容，如果对象是与相同类型的、 从，继承或实现指定的类型。 有关详细信息，请参阅[TypeOf 运算符](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 请注意，指定的类型不能为变量或表达式。 它必须是类型的定义，如类、 结构或接口的名称。 这包括内部类型，如`Integer`和`String`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
