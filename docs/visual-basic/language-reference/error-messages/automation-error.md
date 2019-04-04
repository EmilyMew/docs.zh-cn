---
title: 自动错误
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: e0ebaabb14cf5685469f88b0be3b7fece017165e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843651"
---
# <a name="automation-error"></a>自动错误
执行方法或者获取或设置对象变量的属性时发生错误。 错误由创建该对象的应用程序报告。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查 `Err` 对象的属性，以确定错误来源和错误性质。  
  
2.  在紧邻访问语句之前使用 `On Error Resume Next` 语句，然后检查紧邻访问语句之后是否存在错误。  
  
## <a name="see-also"></a>请参阅

- [错误类型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [与我们交流](/visualstudio/ide/talk-to-us)
