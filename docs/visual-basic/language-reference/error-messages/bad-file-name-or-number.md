---
title: 错误的文件名或文件号
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: b6da1031b60a4cd73c53588cf18992797c3fddab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839062"
---
# <a name="bad-file-name-or-number"></a>错误的文件名或文件号
尝试访问指定的文件时出错。 此错误的可能原因是：  
  
-   语句引用中未指定文件的名称或数字开头的文件`FileOpen`中指定的语句或的`FileOpen`语句但随后被关闭。  
  
-   语句引用的文件数量超出了文件编号的范围。  
  
-   语句引用的文件名或不是有效的数字。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  请确保文件名称中指定`FileOpen`语句。 请注意，如果您调用`FileClose`语句而不使用参数，您可能会无意中关闭所有打开的文件。  
  
2.  如果你的代码通过算法生成文件编号，请确保数字都有效。  
  
3.  检查以确保它们符合操作系统约定的文件名称。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic 命名约定](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
