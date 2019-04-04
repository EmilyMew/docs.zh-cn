---
title: 错误的 DLL 调用约定
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: c4f9917a7fb807cf7da92a3bba2d3edec8045bd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813515"
---
# <a name="bad-dll-calling-convention"></a>错误的 DLL 调用约定
自变量传递给动态链接库 (DLL) 必须完全符合这些例程的要求。 调用约定处理数量、 类型和参数的顺序。 您的程序可能调用例程在传递错误的类型或数量的参数传递的 DLL 中。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  请确保所有参数类型与要调用的例程的声明中指定的都一致。  
  
2.  请确保传递的参数调用的例程的声明中指定的相同数目。  
  
3.  如果 DLL 例程需要按值参数，请确保`ByVal`例程的声明中为这些参数指定。  
  
## <a name="see-also"></a>请参阅

- [错误类型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call 语句](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)
