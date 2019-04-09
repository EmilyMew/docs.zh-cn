---
title: 数组疑难解答 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833368"
---
# <a name="troubleshooting-arrays-visual-basic"></a>数组疑难解答 (Visual Basic)
此页列出了在使用数组时可能发生的一些常见问题。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>编译错误声明和初始化数组  
 编译错误则可能会产生误解的声明、 创建和初始化数组的规则。 错误的最常见原因如下所示：  
  
-   提供[New 运算符](../../../../visual-basic/language-reference/operators/new-operator.md)子句后的数组变量声明中指定维的长度。 下面的代码行显示无效的此类型声明。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   对多个顶级数组交错数组的指定维的长度。 以下代码行显示此类型的一个无效的声明。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略`New`关键字时指定的元素值。 以下代码行显示此类型的一个无效的声明。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   提供`New`子句时没有使用大括号 (`{}`)。 下面的代码行显示无效的此类型声明。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>访问数组超出界限  
 初始化数组的过程将分配给每个维度的上限和下限。 每次访问数组的元素必须指定有效的索引或每个维度的下标。 如果任何索引其下限低于或高于其上限<xref:System.IndexOutOfRangeException>异常结果。 编译器无法检测此类错误，因此在运行时出错。  
  
### <a name="determining-bounds"></a>确定边界  
 如果另一个组件将数组传递给你的代码，例如作为过程自变量，您不知道该数组的大小或它的维的长度。 在尝试访问任何元素之前，您应首先确定数组的每个维度的上限。 如果已通过 Visual Basic 以外的某种方式创建数组`New`子句，更低绑定可能不是 0，并且是最安全，以确定该下限。  
  
### <a name="specifying-the-dimension"></a>指定维度  
 在确定一个多维数组的边界时，请注意如何指定的维度。 `dimension`的参数<xref:System.Array.GetLowerBound%2A>并<xref:System.Array.GetUpperBound%2A>方法是基于 0 的同时`Rank`参数的 Visual Basic<xref:Microsoft.VisualBasic.Information.LBound%2A>和<xref:Microsoft.VisualBasic.Information.UBound%2A>函数都是基于 1 的。  
  
## <a name="see-also"></a>请参阅

- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [如何：初始化数组变量在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
