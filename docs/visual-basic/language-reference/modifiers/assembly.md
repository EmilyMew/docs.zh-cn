---
title: 程序集 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819250"
---
# <a name="assembly-visual-basic"></a>程序集 (Visual Basic)
指定源文件开头特性应用于整个程序集。  
  
## <a name="remarks"></a>备注  
 许多属性适用于单个编程元素，如类或属性。 此类将特性应用通过将附加特性块，在尖括号内 (`< >`)，直接向声明语句。  
  
 如果属性不仅到下面的元素，而且整个程序集，源文件的起始处插入分的特性块和用于标识与特性`Assembly`关键字。 如果应用于当前程序集模块，则使用[模块](../../../visual-basic/language-reference/modifiers/module-keyword.md)关键字。  
  
 您可以还将特性应用于程序集在 AssemblyInfo.vb 文件中，在这种情况下不需要在主源代码文件中使用特性块。  
  
## <a name="see-also"></a>请参阅

- [Module \<关键字>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
