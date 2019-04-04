---
title: 如何：将十六进制字符串转换为数字 (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: 350cfb59a01a4526a2b679fabfa2d49aeab23c19
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813084"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>如何：将十六进制字符串转换为数字 (Visual Basic)
此示例将十六进制字符串转换为整数使用<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>方法。  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>将十六进制字符串转换为数字  
  
-   使用<xref:System.Convert.ToInt32(System.String,System.Int32)>方法将转换为整数的基数为 16 表达的数字。  
  
     第一个参数<xref:System.Convert.ToInt32(System.String,System.Int32)>方法是要转换的字符串。 第二个参数用于描述; 表示的数字的基础十六进制是以 16 为基数。  
  
     [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]  

- 请注意，十六进制字符串有以下限制：

   - 它不能包括`&h`前缀。
   - 它不能包括`_`数字分隔符。

   如果前缀或数字分隔符的存在，调用<xref:System.Convert.ToInt32(System.String,System.Int32)>方法会抛出<xref:System.FormatException>。

## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
