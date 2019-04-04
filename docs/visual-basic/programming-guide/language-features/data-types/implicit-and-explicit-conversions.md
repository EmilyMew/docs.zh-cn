---
title: 隐式转换和显式转换 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833992"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>隐式转换和显式转换 (Visual Basic)
*隐式转换*不需要在源代码中的任何特殊语法。 在以下示例中，Visual Basic 将隐式转换的值`k`为单精度浮点值之前将其分配给`q`。  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *显式转换*使用类型转换关键字。 Visual Basic 提供了此类多个强制转换为所需的数据类型的括号中的表达式的关键字。 这些关键字的行为像函数一样，但编译器生成内联代码，所以执行速度稍快于使用函数调用。  
  
 在上述示例中，以下扩展`CInt`关键字的值转换`q`返回到整数，然后将其分配给`k`。  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>转换关键字  
 下表显示了可用的转换关键字。  
  
|类型转换关键字|将表达式转换为数据类型|允许的数据类型的表达式要转换|  
|---|---|---|  
|`CBool`|[Boolean 数据类型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `String`， `Object`|  
|`CByte`|[Byte 数据类型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任何数值类型 (包括`SByte`和枚举类型)， `Boolean`， `String`， `Object`|  
|`CChar`|[Char 数据类型](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`， `Object`|  
|`CDate`|[Date 数据类型](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`， `Object`|  
|`CDbl`|[Double 数据类型](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CDec`|[Decimal 数据类型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CInt`|[Integer 数据类型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CLng`|[Long 数据类型](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CObj`|[Object 数据类型](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任何类型|  
|`CSByte`|[SByte 数据类型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任何数值类型 (包括`Byte`和枚举类型)， `Boolean`， `String`， `Object`|  
|`CShort`|[Short 数据类型](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CSng`|[Single 数据类型](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CStr`|[String 数据类型](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `Char`，`Char`数组， `Date`， `Object`|  
|`CType`|逗号后面指定的类型 (`,`)|将转换为时*基本数据类型*（包括基本类型的数组），相同类型允许的相应的转换关键字<br /><br /> 将转换为时*复合数据类型*，它实现的接口和它所继承的类<br /><br /> 将转换为在其上具有重载的类或结构时`CType`，该类或结构|  
|`CUInt`|[UInteger 数据类型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CULng`|[ULong 数据类型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
|`CUShort`|[UShort 数据类型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任何数值类型 (包括`Byte`， `SByte`，并枚举类型)， `Boolean`， `String`， `Object`|  
  
## <a name="the-ctype-function"></a>CType 函数  
 [CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)对两个自变量进行操作。 第一个是要转换的表达式，第二个参数是目标数据类型或对象类。 请注意，第一个参数必须是一个表达式，而不是类型。  
  
 `CType` 是*内联函数*，这意味着已编译的代码可以进行转换，通常不会生成一个函数调用。 这可以提高性能。  
  
 有关的比较`CType`与其他类型转换关键字，请参阅[DirectCast 运算符](../../../../visual-basic/language-reference/operators/directcast-operator.md)并[TryCast 运算符](../../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
### <a name="elementary-types"></a>基本类型  
 以下示例演示了 `CType` 的用法。  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>复合类型  
 可以使用`CType`将值转换为复合数据类型以及基本类型。 此外可以使用它要强制转换为其中一个接口，如以下示例所示的类型的对象类。  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>数组类型  
 `CType` 也可以转换数组数据类型，如以下示例所示。  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 有关详细信息和示例，请参阅[数组转换](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。  
  
### <a name="types-defining-ctype"></a>定义 CType 类型  
 您可以定义`CType`上类或结构定义。 这可以与类或结构的类型转换的值。 有关详细信息和示例，请参阅[如何：定义转换运算符](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
> [!NOTE]
>  与转换关键字一起使用的值必须是有效的目标数据类型，否则将出错。 例如，如果你尝试转换`Long`到`Integer`的值`Long`必须在有效范围内`Integer`数据类型。  
  
> [!CAUTION]
>  指定`CType`如果源类型不从目标类型派生一个类类型从转换为另一个将在运行时失败。 此类故障引发<xref:System.InvalidCastException>异常。  
  
 但是，如果一种类型的结构或类定义后，并已定义`CType`在该结构或类上，如果它满足的要求转换才能成功你`CType`。 请参阅[如何：定义转换运算符](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
 执行的显式转换也称为非常*强制转换*为给定的数据类型或对象类的表达式。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [字符串和其他类型之间的转换](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：将对象转换为 Visual Basic 中的另一种类型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [结构](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
