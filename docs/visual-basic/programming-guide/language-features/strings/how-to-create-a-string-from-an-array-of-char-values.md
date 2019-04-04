---
title: 如何：从 Char 值 (Visual Basic 中) 的数组创建字符串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 1f72cb86ffa38dc929062fab2f5592a781f2de27
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831821"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>如何：从 Char 值 (Visual Basic 中) 的数组创建字符串
此示例创建从单独的字符的字符串"abcd"。  
  
## <a name="example"></a>示例  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此方法具有任何特殊要求。  
  
 语法`"a"c`，其中单个`c`跟随在引号内的单个字符，用于创建字符文本。  
  
## <a name="robust-programming"></a>可靠编程  
 Null 字符 (等效于`Chr(0)`) 在字符串中会导致意外结果时使用的字符串。 Null 字符将包含在字符串中，但在某些情况下将不会显示在 null 字符后面的字符。  
  
## <a name="see-also"></a>请参阅

- <xref:System.String>
- [Char 数据类型](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
