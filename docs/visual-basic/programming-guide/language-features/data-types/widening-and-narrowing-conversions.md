---
title: 扩大转换和收缩转换 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: 9f1a71e8e2e3e4ebb9b412be74b5ea8702eb164f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842546"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>扩大转换和收缩转换 (Visual Basic)
类型转换的一个重要考虑因素是转换的结果是否在目标数据类型的范围内。  
  
 一个*扩大转换*值更改为可实现任何可能值的原始数据的数据类型。  扩大转换保留源值，但可以更改它的表示形式。 发生这种情况是如果将从整型类型转换`Decimal`，或从`Char`到`String`。  
  
 *“收缩转换”* 将值更改为可能无法保存某些可能值的数据类型。 小数部分值转换为整型类型，并转换为数值类型时，舍入`Boolean`减少至任一`True`或`False`。  
  
## <a name="widening-conversions"></a>扩大转换  
 下表显示了标准的扩大转换。  
  
|数据类型|扩大的数据类型为<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[小数](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`， `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|任何枚举类型 ([枚举](../../../../visual-basic/language-reference/statements/enum-statement.md))|其基础整型类型和任何类型的基础类型扩大。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`， `String`|  
|`Char` 数组|`Char` 数组， `String`|  
|任何类型|[Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|任何派生的类型|任何基的类型派生自<sup>3</sup>。|  
|任何类型|它实现任何接口。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任何数据类型或对象类型。|  
  
 <sup>1</sup>根据定义，每个数据类型加宽到本身。  
  
 <sup>2</sup>从小`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`到`Single`或`Double`可能导致丢失精度，但永远不会导致丢失量值。 在这种情况下它们不会产生信息丢失。  
  
 <sup>3</sup>它可能看起来令人惊讶的扩大转换从派生类型转换为其基类型之一。 理由是派生的类型包含基类型的所有成员，因此它被称为基类型的实例。 在相反方向的基类型不包含由派生的类型定义任何新成员。  
  
 扩大转换在运行时始终成功，并且永远不会导致数据丢失。 始终可以隐式执行它们，是否[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)设置类型检查开关`On`或`Off`。  
  
## <a name="narrowing-conversions"></a>收缩转换  
 标准的收缩转换如下所示：  
  
-   在前面的扩大转换的相反方向表 （不过，每个类型扩大到自身）  
  
-   在任一方向之间的转换[布尔](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)和任何数值类型  
  
-   从任何数值类型转换为任何枚举类型 (`Enum`)  
  
-   在任一方向之间的转换[字符串](../../../../visual-basic/language-reference/data-types/string-data-type.md)和任何数值类型`Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   从数据类型或对象类型转换为其派生的类型  
  
 收缩转换执行不总是在运行时，成功和可以故障或会导致数据丢失。 如果目标数据类型不能接收要转换的值，就会出错。 例如，数值的转换导致溢出。 编译器不允许您以隐式执行收缩转换，除非[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)设置类型检查开关`Off`。  
  
> [!NOTE]
>  收缩转换错误则会取消对从中的元素的转换`For Each…Next`循环控制变量的集合。 有关详细信息和示例，请参阅中的"收缩转换"部分[为每个...下一条语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="when-to-use-narrowing-conversions"></a>何时使用收缩转换  
 当您知道源值可以转换为无错误或数据丢失的目标数据类型时使用收缩转换。 例如，如果你有`String`，您知道包含"True"False"，您可以使用`CBool`关键字将其转换为`Boolean`。  
  
## <a name="exceptions-during-conversion"></a>转换期间的异常  
 由于扩大转换始终成功，它们不会引发异常。 收缩转换，在故障时最常引发以下异常：  
  
-   <xref:System.InvalidCastException> -如果两个类型之间不定义任何转换  
  
-   <xref:System.OverflowException> -（仅限整型） 如果转换后的值的目标类型太大  
  
 如果类或结构定义了[CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)转换运算符到或从该类或结构，作为的`CType`可以引发任何它认为适当的任何异常。 此外，该`CType`可能会调用 Visual Basic 函数或[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]又可能会引发多种异常的方法。  
  
## <a name="changes-during-reference-type-conversions"></a>引用类型转换过程中的更改  
 从转换*引用类型*只复制的指针的值。 值本身不复制也不以任何方式更改。 可以更改的唯一事情是变量的包含指针的数据类型。 在以下示例中，数据类型从派生类转换为它的基类，但这两个变量现在指向的对象保持不变。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>请参阅

- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [在 Visual Basic 中的类型转换](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [隐式转换和显式转换](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字符串和其他类型之间的转换](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：将对象转换为 Visual Basic 中的另一种类型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [数组转换](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
