---
title: 对象变量值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: c17c5f85952596f0a080ca473e8f792740e66b8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840388"
---
# <a name="object-variable-values-visual-basic"></a>对象变量值 (Visual Basic)
变量[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)可以指任何类型的数据。 在中存储的值`Object`变量保存到其他位置在内存中，而变量本身保存一个指针，该数据。  
  
## <a name="object-classifier-functions"></a>对象的分类器函数  
 Visual Basic 提供的函数可返回有关的内容信息`Object`变量所引用下, 表中所示。  
  
|函数|如果对象变量引用的则返回 True|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|一个值，而不是单个值的数组|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|一个[日期数据类型](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解释为日期和时间值的字符串|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|类型的对象<xref:System.DBNull>，表示缺失或不存在的数据|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|一个异常对象，它派生自 <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[执行任何操作](../../../../visual-basic/language-reference/nothing.md)，没有任何对象，它是当前分配给变量|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|一个数字或可以解释为数字的字符串|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|引用类型 （如字符串、 数组、 委托或类类型）|  
  
 这些函数可用于避免提交至操作或过程的无效值。  
  
## <a name="typeof-operator"></a>TypeOf 运算符  
 此外可以使用[TypeOf 运算符](../../../../visual-basic/language-reference/operators/typeof-operator.md)来确定为特定的数据类型是否当前引用的对象变量。 `TypeOf`...`Is`表达式的计算结果为`True`如果操作数的运行时类型派生自或实现指定的类型。  
  
 下面的示例使用`TypeOf`引用值和引用类型的对象变量上。  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 前面的示例将以下行**调试**窗口：  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 对象变量`num`类型的数据是指`Integer`，并`frm`类的对象是指<xref:System.Windows.Forms.Form>。  
  
## <a name="object-arrays"></a>对象数组  
 您可以声明和使用数组`Object`变量。 当您需要处理各种数据类型和对象类时，这很有用。 数组中的所有元素必须都具有相同的声明的数据类型。 声明此数据类型为`Object`可以用于存储对象和类实例及其他数组中的数据类型。  
  
## <a name="see-also"></a>请参阅

- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量声明](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [对象变量赋值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [如何：引用对象的当前实例](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [如何：确定对象变量引用的类型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [如何：确定两个对象是否相关](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [如何：确定两个对象是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
