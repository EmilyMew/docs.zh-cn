---
title: Array Dimensions in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836930"
---
# <a name="array-dimensions-in-visual-basic"></a>Array Dimensions in Visual Basic
一个*维度*是在其中您可以更改数组的元素的规范的方向。 一个数组，其中保存总销量，月份中的每一天有一个维度 （每月天数）。 保存总销量由部门的月份中的每一天的数组具有两个维度 （部门编号和每月天数）。 名为的维数的数组具有其*排名*。  
  
> [!NOTE]
>  可以使用<xref:System.Array.Rank%2A>属性来确定多少维数的数组具有。  
  
## <a name="working-with-dimensions"></a>使用的维度  
 通过提供指定数组的元素*索引*或*下标*为每个维度。 元素是从 0 到最高的索引，该维度连续沿每个维度。  
  
 下图显示具有不同秩的数组的概念结构。 在图例中的每个元素显示对其进行访问的索引值。 例如，可以通过指定索引访问的二维数组的第二个行的第一个元素`(1, 0)`。  
  
 ![图，显示一个一维数组。](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![图，显示一个二维数组。](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![图，显示三维数组。](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a>一个维度  
 多个数组具有只有一个维度，例如每个年龄的用户数。 若要指定的元素的唯一要求是该元素为其保留计数的年龄。 因此，此类数组使用只有一个索引。 下面的示例声明一个变量来保存*的一维数组*于阶段 0 到 120 计数的年龄。  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a>两个维度  
 某些数组具有两个维度，如在校园上每个生成的每个楼层机构数量。 元素的规范要求的建筑号和基底，并且每个元素均包含构造和层的组合的计数。 因此，此类数组使用两个索引。 下面的示例声明一个变量来保存*二维数组*office 计数，0 到 40 建筑和楼层从 0 到 5。  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 二维数组也称为*矩形数组*。  
  
### <a name="three-dimensions"></a>三个维度  
 几个数组具有三个维度，如三维空间中的值。 一个数组，此类使用三个索引，在这种情况下表示 x、 y 和 z 坐标的物理空间。 下面的示例声明一个变量来保存*三维数组*的气温三维卷中的不同位置。  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a>超过三个维度  
 虽然数组可以有多达 32 维数，很少会有三个。  
  
> [!NOTE]
>  当将维度添加到一个数组时，数组所需的总存储会急剧增大，因此谨慎使用多维数组。  
  
## <a name="using-different-dimensions"></a>使用不同的维度  
 假设您想要跟踪的每一天的存在月销售额。 可能会声明 31 元素的一维数组，一个用于每一天的月份，如下面的示例显示了。  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 现在假设你想要跟踪不仅对每一天的每个月，但还为一年中的每个月的相同信息。 如以下示例所示，可能会声明一个二维数组具有 12 行 （适用于几个月） 和 （对于天），31 列。  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 现在假设你决定让你的数组将保存多个为一年的信息。 如果你想要跟踪的 5 年的销售额，您可能如以下示例所示声明具有 5 层、 12 行和 31 列的三维数组。  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 注意，因为每个索引值从 0 到变化其最大值，每个维度的`salesAmounts`该维度被声明为一个小于所需的长度。 另请注意，数组的大小会增加与每个新的维度。 在上述示例中的三个大小分别为 31、 372 和 1860 个元素。  
  
> [!NOTE]
>  您可以创建一个数组，而无需使用`Dim`语句或`New`子句。 例如，可以调用<xref:System.Array.CreateInstance%2A>方法或另一个组件可以通过你的代码以这种方式创建的数组。 此类数组可以有 0 以外的下限。 始终可以通过使用测试维度的下限<xref:System.Array.GetLowerBound%2A>方法或`LBound`函数。  
  
## <a name="see-also"></a>请参阅

- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
