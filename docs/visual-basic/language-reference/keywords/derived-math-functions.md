---
title: 派生的数学函数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836579"
---
# <a name="derived-math-functions-visual-basic"></a>派生的数学函数 (Visual Basic)
下表显示了可以派生自的内部函数的数学函数的非内部函数的数学函数<xref:System.Math?displayProperty=nameWithType>对象。 可以通过添加访问内部函数的数学函数`Imports System.Math`到文件或项目。  
  
|函数|派生的等效项|  
|--------------|-------------------------|  
|正割值 (Sec(x))|1 / Cos(x)|  
|余割值 (Csc(x))|1 / Sin(x)|  
|余切值 (Ctan(x))|1 / Tan(x)|  
|反正弦值 (Asin(x))|Atan (x / Sqrt (-x * x + 1))|  
|反余弦值 (Acos(x))|Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)|  
|反正割 (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))|  
|反余割值 (Acsc(x))|Atan(Sign(x) / Sqrt (x * x – 1))|  
|反余切值 (Acot(x))|2 * Atan(1) - Atan(x)|  
|双曲正弦值 (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|双曲余弦值 (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|双曲正切值 (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|双曲正割值 (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|双曲余割值 (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|双曲余切值 (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|反双曲正弦值 (Asinh(x))|日志 (x + Sqrt (x * x + 1))|  
|反双曲余弦值 (Acosh(x))|日志 (x + Sqrt (x * x – 1))|  
|反双曲正切值 (Atanh(x))|日志 ((1 + x) / (1 – x)) / 2|  
|反双曲正割值 (AsecH(x))|Log ((Sqrt (-x * x + 1) + 1) / x)|  
|反双曲余割值 (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|反双曲余切值 (Acoth(x))|日志 ((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>请参阅

- [数学函数](../../../visual-basic/language-reference/functions/math-functions.md)
