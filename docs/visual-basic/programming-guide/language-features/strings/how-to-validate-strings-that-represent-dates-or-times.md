---
title: 如何：验证表示日期或时间的字符串 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f24ff05e48327c21c02eb92b07db17266f743a80
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815225"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>如何：验证表示日期或时间的字符串 (Visual Basic)
下面的代码示例设置`Boolean`值，该值指示字符串是否表示有效的日期或时间。  
  
## <a name="example"></a>示例  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>编译代码  
 替换`("01/01/03")`和`"9:30 PM"`使用日期和你想要验证的时间。 您可以将使用另一个硬编码字符串、 字符串替换为`String`变量，或使用一种方法，返回一个字符串，如`InputBox`。  
  
## <a name="robust-programming"></a>可靠编程  
 使用此方法尝试转换之前验证字符串`String`到`DateTime`变量。 通过首先检查包含日期或时间，可以避免生成在运行时异常。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [在 Visual Basic 中验证字符串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
