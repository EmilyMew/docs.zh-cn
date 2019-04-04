---
title: 如何：确定与枚举值 (Visual Basic 中) 关联的字符串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4fa04fa621347ae961975bfb636734e6c9df39fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829208"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>如何：确定与枚举值 (Visual Basic 中) 关联的字符串
<xref:System.Enum.GetValues%2A>和<xref:System.Enum.GetNames%2A>方法可用于确定字符串和枚举成员与相关联的值。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>若要确定与枚举关联的字符串  
  
-   使用<xref:System.Enum.GetNames%2A>方法来检索与枚举成员关联的字符串。 此示例中声明枚举，这`flavorEnum`，然后使用<xref:System.Enum.GetNames%2A>方法来显示与每个成员关联的字符串。  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：循环访问在 Visual Basic 中枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [何时使用枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum 语句](../../../../visual-basic/language-reference/statements/enum-statement.md)
