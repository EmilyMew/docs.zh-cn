---
title: 如何：循环访问在 Visual Basic 中枚举
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 63597145e96b04affc5f0e80e05a56b3fdf27278
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833355"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>如何：循环访问在 Visual Basic 中枚举
枚举提供了使用相关常量集以及将常量值与名称相关联的一个便捷方法。 若要循环访问枚举，可以将为数组，并使用它<xref:System.Enum.GetValues%2A>方法。 您还可以通过枚举使用迭代`For...Each`语句中，使用<xref:System.Enum.GetNames%2A>或<xref:System.Enum.GetValues%2A>方法提取字符串或数字值。  
  
### <a name="to-iterate-through-an-enumeration"></a>若要循环访问枚举  
  
-   声明数组并将枚举转换为其与<xref:System.Enum.GetValues%2A>然后再将数组传递作为您的方法将任何其他变量。 下面的示例显示枚举的每个成员<xref:Microsoft.VisualBasic.FirstDayOfWeek>如循环枚举。  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>请参阅

- [枚举概述](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [何时使用枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [如何：确定与枚举值关联的字符串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
