---
title: 对象数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835565"
---
# <a name="object-data-type"></a>Object Data Type
保存引用的对象的地址。 可以将任何引用类型 （字符串、 数组、 类或接口） 分配给`Object`变量。 `Object`变量还可以指任何值类型的数据 (数字`Boolean`， `Char`， `Date`，结构或枚举)。  
  
## <a name="remarks"></a>备注  
 `Object`数据类型可以指向任何数据类型，包括你的应用程序可以识别的任何对象实例的数据。 使用`Object`时您在编译时不知道哪种数据类型变量可能指向。  
  
 默认值`Object`是`Nothing`（空引用）。  
  
## <a name="data-types"></a>数据类型  
 可以分配变量、 常量或表达式的任何数据类型设置为`Object`变量。 若要确定数据类型`Object`变量当前引用的则可以使用<xref:System.Type.GetTypeCode%2A>方法的<xref:System.Type?displayProperty=nameWithType>类。 下面的示例阐释了这一点。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object`数据类型为引用类型。 但是，Visual Basic 处理`Object`变量作为值类型时它指的是值类型的数据。  
  
## <a name="storage"></a>存储  
 它指任何数据类型`Object`变量不包含数据值本身，但而不是指向值的指针。 它始终在计算机内存中，使用四个字节，但这不包括表示变量的值的数据的存储。 使用指针来定位数据的代码由于`Object`持有值类型变量时速度稍慢访问比显式类型化的变量。  
  
## <a name="programming-tips"></a>编程提示  
  
-   **互操作注意事项。** 如果你与不是为.NET Framework 中，如自动化或 COM 对象，编写组件交互请记住在其他环境中的指针类型不兼容使用 Visual Basic`Object`类型。  
  
-   **性能。** 使用声明的变量`Object`类型非常灵活，可以包含对任何对象的引用。 但是，当您调用的方法或属性的此类变量，则始终会产生*后期绑定*（在运行时）。 若要强制*早期绑定*（在编译时） 和更好的性能、 使用特定的类名称，将变量声明，或将其转换为特定的数据类型。  
  
     当声明对象变量时，请尝试使用特定的类类型，例如<xref:System.OperatingSystem>，而不是通用`Object`类型。 此外应使用最具体的类可用，如<xref:System.Windows.Forms.TextBox>而不是<xref:System.Windows.Forms.Control>，以便可以访问其属性和方法。 您通常可以使用**类**列表中**对象浏览器**来查找可用的类名称。  
  
-   **扩大转换。** 所有数据类型和所有引用类型扩大到`Object`数据类型。 这意味着可以将转换为任何类型`Object`而不会遇到<xref:System.OverflowException?displayProperty=nameWithType>错误。  
  
     但是，如果值类型之间转换并`Object`，Visual Basic 执行调用的操作*装箱*并*取消装箱*，这使执行速度更慢。  
  
-   **类型字符。** `Object` 不包含文本类型字符或标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是<xref:System.Object?displayProperty=nameWithType>类。  
  
## <a name="example"></a>示例  
 下面的示例演示`Object`变量指向的对象实例。  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Object>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [如何：确定两个对象是否相关](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [如何：确定两个对象是否相同](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
