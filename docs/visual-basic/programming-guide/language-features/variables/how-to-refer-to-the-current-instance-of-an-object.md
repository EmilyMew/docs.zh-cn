---
title: 如何：引用的对象 (Visual Basic 中) 的当前实例
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823358"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>如何：引用的对象 (Visual Basic 中) 的当前实例
*当前实例*的对象是当前正在其中执行代码的实例。  
  
 您使用`Me`关键字来引用当前实例。  
  
### <a name="to-refer-to-the-current-instance"></a>若要引用的当前实例  
  
-   使用`Me`关键字，通常会使用对象变量的名称。  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     尽管`Me`的行为类似于对象变量时，不能将其声明或向其分配的任何内容。 `Me` 始终引用当前实例。  
  
## <a name="see-also"></a>请参阅

- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量赋值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
