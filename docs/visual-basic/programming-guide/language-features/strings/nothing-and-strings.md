---
title: Nothing 和字符串 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841883"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nothing 和字符串 (Visual Basic)
Visual Basic 运行时，[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]评估`Nothing`以不同的方式时涉及到字符串。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 运行时和.NET Framework  
 请看下面的示例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 运行时通常计算结果`Nothing`为空字符串 ("")。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]但是，不，不会引发异常，只要尝试对其执行字符串操作`Nothing`。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的字符串简介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
