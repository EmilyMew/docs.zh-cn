---
title: 如何：将数据移入和移出变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818524"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>如何：将数据移入和移出变量 (Visual Basic)
通过将变量名称放在赋值语句左侧，可以在变量中存储值。  
  
## <a name="putting-data-in-a-variable"></a>将数据放在变量中  
  
#### <a name="to-store-a-value-in-a-variable"></a>若要在变量中存储的值  
  
-   在赋值语句左侧使用变量的名称。  
  
     下面的示例设置变量的值`alpha`。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     生成的赋值语句右侧的值存储在变量中。  
  
## <a name="getting-data-from-a-variable"></a>从变量中获取数据  
 通过将变量名称包含在表达式中检索变量的值。  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>若要从变量检索值  
  
-   在表达式中使用的变量名称。 您可以使用变量任何可以使用常量或文本，除中定义的常量的值的表达式。  
  
     或  
  
-   使用以下等号的变量名称 (`=`) 在赋值语句登录。  
  
     下面的示例读取该变量的值`startValue`，然后使用该变量的值`counter`在表达式中。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     变量的值参与到表达式，就像做一个常量，而且则存储在变量或赋值语句左侧的属性。  
  
## <a name="see-also"></a>请参阅

- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
