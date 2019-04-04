---
title: 如何：将字符串转换成 Visual Basic 中的字节数组
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 2fa0b86459e6191d3bd5f884d92b071218b4063a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823267"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>如何：将字符串转换成 Visual Basic 中的字节数组
本主题演示如何将字符串转换为一个字节的数组。  
  
## <a name="example"></a>示例  
 此示例使用<xref:System.Text.Encoding.GetBytes%2A>方法的<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>编码类将字符串转换为一个字节的数组。  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 你可以从多个编码选项，将字符串转换为字节数组中进行选择：  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：获取 ASCII（7 位）字符集的编码。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：获取使用 big endian 字节顺序的 utf-16 格式的编码。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：获取系统的当前 ANSI 代码页的编码。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：获取使用 little-endian 字节顺序的 utf-16 格式的编码。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：获取使用 little-endian 字节顺序的 UTF-32 格式的编码。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：获取 UTF-7 格式的编码。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：获取 UTF-8 格式的编码。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [如何：将一个字节数组转换成 Visual Basic 中的字符串](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
