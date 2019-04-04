---
title: 如何：组相关的常量值组合在一起 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 9174bcd2385103cf7fa1daf3133e388f9b4998a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843755"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>如何：组相关的常量值组合在一起 (Visual Basic)
枚举是要分成一组相关的常量的最佳方式。 创建一个枚举，其中`Enum`声明部分中的一个类或模块的语句。 有关详细信息，请参阅[如何：声明枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)。  
  
### <a name="to-group-related-constant-values"></a>向组相关的常量值  
  
1.  编写的声明，包括代码访问级别，`Enum`关键字，并且是有效的名称。 此示例将创建`Private`枚举， `temperatureValues`。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  枚举中定义常量。 此示例将创建`Public`枚举`temperatureValues`并为其赋值。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>请参阅

- [枚举和名称限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：为枚举成员，请参阅](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [何时使用枚举](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常量概述](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [常量和文本数据类型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常量和枚举](../../../../visual-basic/language-reference/constants-and-enumerations.md)
