---
title: 如何：在 Visual Basic 中的字符串中的访问字符
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834486"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>如何：在 Visual Basic 中的字符串中的访问字符
此示例演示如何使用<xref:System.String.Chars%2A>属性来访问位于字符串中的指定位置处的字符。  
  
## <a name="example"></a>示例  
 有时是有关你的字符串和这些字符在字符串中的位置中的字符的数据很有用。 您可以将字符串视为字符数组 (`Char`实例); 您可以通过引用通过该字符的索引检索特定字符<xref:System.String.Chars%2A>属性。  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`参数的<xref:System.String.Chars%2A>属性是从零开始。  
  
## <a name="robust-programming"></a>可靠编程  
 <xref:System.String.Chars%2A>属性返回位于指定位置处的字符。 但是，可以由多个字符表示的某些 Unicode 字符。 有关如何使用 Unicode 字符的详细信息，请参阅[如何：将字符串转换为字符数组](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。  
  
 <xref:System.String.Chars%2A>属性，则会引发<xref:System.IndexOutOfRangeException>异常如果`index`参数是否大于或等于字符串的长度，或如果它小于零  
  
## <a name="see-also"></a>请参阅

- <xref:System.String.Chars%2A>
- [如何：将字符串转换为字符数组](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [在 Visual Basic 中将字符串转换为其他数据类型](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [字符串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
