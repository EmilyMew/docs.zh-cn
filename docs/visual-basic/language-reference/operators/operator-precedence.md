---
title: Visual Basic 中的运算符优先级
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 568927eb4759c214311ad34a5b45e28094dd80be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830027"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的运算符优先级
如果在表达式中出现多个运算，每个部分进行计算，并在预先确定的顺序调用中解析*运算符优先级*。  
  
## <a name="precedence-rules"></a>优先规则  
 当表达式包含多个类别中的运算符时，它们会根据以下规则进行评估：  
  
-   算术运算和串联运算符具有下面部分中所述的优先顺序，都具有更高的优先级高于比较、 逻辑和位运算符。  
  
-   所有比较运算符都具有相同的优先级，以及所有都具有更高的优先级高于逻辑运算符和位运算符，但算术运算和串联运算符的优先顺序更低。  
  
-   逻辑和位运算符具有下面部分中所述的优先顺序，并且所有优先级低于算术运算符、 串联和比较运算符。  
  
-   具有相同的优先级的运算符左到右求值表达式中出现的顺序。  
  
## <a name="precedence-order"></a>优先顺序  
 运算符按以下优先顺序计算：  
  
### <a name="await-operator"></a>Await 运算符  
 Await  
  
### <a name="arithmetic-and-concatenation-operators"></a>算术运算符和串联运算符  
 求幂 (`^`)  
  
 一元标识和求反 (`+`， `–`)  
  
 乘法和浮点除法 (`*`， `/`)  
  
 整数除法 (`\`)  
  
 取模算术 (`Mod`)  
  
 加法和减法 (`+`， `–`)  
  
 字符串串联 (`&`)  
  
 算术移位 (`<<`， `>>`)  
  
### <a name="comparison-operators"></a>比较运算符  
 所有比较运算符 (`=`， `<>`， `<`， `<=`， `>`， `>=`， `Is`， `IsNot`， `Like`， `TypeOf`...`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>逻辑运算符和位运算符  
 求反 (`Not`)  
  
 一起使用 (`And`， `AndAlso`)  
  
 包含析取 (`Or`， `OrElse`)  
  
 异或运算 (`Xor`)  
  
### <a name="comments"></a>注释  
 `=`运算符只是相等性比较运算符，不是赋值运算符。  
  
 字符串串联运算符 (`&`) 不是算术运算符，但它在优先级方面与算术运算符一组。  
  
 `Is`和`IsNot`运算符是对象的引用比较运算符。 它们不比较两个对象; 的值它们检查仅以确定两个对象变量是否引用相同的对象实例。  
  
## <a name="associativity"></a>结合性  
 当相同优先级的运算符一起出现在表达式中，例如乘法和除法，编译器将计算每个操作遇到它从左到右。 下面的示例阐释了这一点。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 第一个表达式的计算结果除法 96 / 8 （这会导致 12），然后划分为 12 / 4 中，这样，在三个。 由于编译器将计算的操作`n1`计算从左到右，是相同的显式指示该顺序`n2`。 这两`n1`和`n2`具有三个结果。 与此相反，`n3`的结果为 48，是因为在圆括号强制编译器可以计算 8 / 4 第一个。  
  
 由于此行为，运算符被称为*左结合运算符*在 Visual Basic 中。  
  
## <a name="overriding-precedence-and-associativity"></a>重写优先级和结合性  
 可以使用括号强制先于其他计算的表达式的某些部分。 这可重写的优先顺序和左的关联性。 Visual Basic 始终执行括在括号外之前的操作。 但是，在括号内，它将保留普通优先级和关联性，除非使用括号中的括号。 下面的示例阐释了这一点。  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>请参阅

- [= 运算符](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like 运算符](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf 运算符](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await 运算符](../../../visual-basic/language-reference/operators/await-operator.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
