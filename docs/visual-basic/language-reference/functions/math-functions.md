---
title: 数学函数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: e5f87a8e367e8c9df65b979fea3781b42ee3ce83
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824957"
---
# <a name="math-functions-visual-basic"></a>数学函数 (Visual Basic)
方法<xref:System.Math?displayProperty=nameWithType>类提供三角、 对数和其他通用数学函数。  
  
## <a name="remarks"></a>备注  
 下表列出了方法的<xref:System.Math?displayProperty=nameWithType>类。 您可以使用这些在 Visual Basic 程序中。  
  
|.NET 方法|描述|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|返回数字的绝对值。|  
|<xref:System.Math.Acos%2A>|返回余弦值为指定数字的角度。|  
|<xref:System.Math.Asin%2A>|返回正弦值为指定数字的角度。|  
|<xref:System.Math.Atan%2A>|返回正切值为指定数字的角度。|  
|<xref:System.Math.Atan2%2A>|返回正切值为两个指定数字的商的角度。|  
|<xref:System.Math.BigMul%2A>|返回两个 32 位数字的完整的产品。|  
|<xref:System.Math.Ceiling%2A>|返回大于或等于指定的最小整数值`Decimal`或`Double`。|  
|<xref:System.Math.Cos%2A>|返回指定角度的余弦值。|  
|<xref:System.Math.Cosh%2A>|返回指定角度的双曲余弦值。|  
|<xref:System.Math.DivRem%2A>|返回两个 32 位或 64 位有符号整数的商和输出参数中返回余数。|  
|<xref:System.Math.Exp%2A>|返回 e （自然对数的底数） 指定次幂。|  
|<xref:System.Math.Floor%2A>|返回小于或等于指定的最大整数`Decimal`或`Double`数。|  
|<xref:System.Math.IEEERemainder%2A>|返回由另一个相除所得的指定数量的其余部分指定的数量。|  
|<xref:System.Math.Log%2A>|在使用指定底返回指定数字的自然 （以 e） 对数或指定数量的对数。|  
|<xref:System.Math.Log10%2A>|返回指定数字以 10 为底的对数。|  
|<xref:System.Math.Max%2A>|返回较大的两个数字。|  
|<xref:System.Math.Min%2A>|返回两个数字中较小的一个。|  
|<xref:System.Math.Pow%2A>|返回指定数字的指定次幂。|  
|<xref:System.Math.Round%2A>|返回`Decimal`或`Double`值舍入为最接近的整数值或指定数量的小数位数。|  
|<xref:System.Math.Sign%2A>|返回`Integer`值，该值指示数字的符号。|  
|<xref:System.Math.Sin%2A>|返回指定角度的正弦值。|  
|<xref:System.Math.Sinh%2A>|返回指定角度的双曲正弦值。|  
|<xref:System.Math.Sqrt%2A>|返回指定数字的平方根。|  
|<xref:System.Math.Tan%2A>|返回指定角度的正切值。|  
|<xref:System.Math.Tanh%2A>|返回指定角度的双曲正切值。|  
|<xref:System.Math.Truncate%2A>|计算指定的整数部分`Decimal`或`Double`数。|  
  
 若要使用这些函数而无需限定，导入<xref:System.Math?displayProperty=nameWithType>到项目中通过将以下代码添加到源文件顶部的命名空间：  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Abs%2A>方法的<xref:System.Math>类，以计算一个数字的绝对值。  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Atan%2A>方法的<xref:System.Math>类来计算 pi 的值。  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Cos%2A>方法的<xref:System.Math>类以返回角度的余弦值。  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Exp%2A>方法的<xref:System.Math>类以返回 e 的幂。  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Log%2A>方法的<xref:System.Math>类，以返回一个数字的自然对数。  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Round%2A>方法的<xref:System.Math>类要舍入到最接近的整数的数字。  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Sign%2A>方法的<xref:System.Math>类来确定数字的符号。  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Sin%2A>方法的<xref:System.Math>类以返回角度的正弦值。  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Sqrt%2A>方法的<xref:System.Math>类，以计算一个数字的平方根。  
  
```vb
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Math.Tan%2A>方法的<xref:System.Math>类以返回角度的正切值。  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>要求  
 **类：** <xref:System.Math>  
  
 **Namespace**：<xref:System>  
  
 **程序集：** mscorlib （在 mscorlib.dll 中)  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [派生的数学函数](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
