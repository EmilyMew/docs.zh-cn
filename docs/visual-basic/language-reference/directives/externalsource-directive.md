---
title: '#ExternalSource 指令 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823423"
---
# <a name="externalsource-directive"></a>#ExternalSource 指令
指示特定行的源代码和源的外部文本之间的映射。  
  
## <a name="syntax"></a>语法  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>部件  
 `StringLiteral`  
 指向外部源的路径。  
  
 `IntLiteral`  
 外部源的第一行的行数。  
  
 `LogicalLine`  
 外部源中发生错误的行。  
  
 `#End ExternalSource`  
 终止 `#ExternalSource` 块。  
  
## <a name="remarks"></a>备注  
 使用此指令时仅由编译器和调试器。  
  
 源代码文件可以包含外部源指令，指示特定行的源文件中的代码和源，例如.aspx 文件的外部文本之间的映射。 如果在编译期间指定的源代码中遇到错误，则将其标识为来自外部源中。  
  
 外部源指令不会影响编译，而且不能嵌套。 它们是由应用程序仅供内部使用。  
  
## <a name="see-also"></a>请参阅

- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
