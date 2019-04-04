---
title: 如何：在 Visual Basic 中的对数组进行排序
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838074"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>如何：在 Visual Basic 中的对数组进行排序
此示例中声明的数组`String`对象名为`zooAnimals`，填充它，而按字母顺序排序。  
  
## <a name="example"></a>示例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 Mscorlib.dll 的访问和<xref:System>命名空间。  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会导致异常：  
  
-   数组为空 (<xref:System.ArgumentNullException>类)  
  
-   数组是多维数组 (<xref:System.RankException>类)  
  
-   数组的一个或多个元素不实现<xref:System.IComparable>接口 (<xref:System.InvalidOperationException>类)  
  
## <a name="see-also"></a>请参阅

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [集合](../../concepts/collections.md)
- [For Each...Next 语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
