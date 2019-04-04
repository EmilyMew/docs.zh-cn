---
title: 该“Sub New”的第一个语句必须是对“MyBase.New”或“MyClass.New”的调用（没有不带参数的可访问构造函数）
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: debab4e495d05a05801dd11850d0665c8bd6b299
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834317"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>该“Sub New”的第一个语句必须是对“MyBase.New”或“MyClass.New”的调用（没有不带参数的可访问构造函数）
此 Sub New 的第一个语句必须是对 MyBase.New 或 MyClass.New 的调用，因为基类 '\<basename > 的\<derivedname > 不具有可访问 Sub New，可以调用不带任何参数。  
  
 在派生类中，每个构造函数必须调用基类构造函数 (`MyBase.New`)。 如果基类具有不带任何参数是可用于派生类的构造函数`MyBase.New`可以自动调用。 如果没有，则必须使用参数，调用基类构造函数，这不能自动完成。 在这种情况下，每个派生的类构造函数的第一个语句必须在基础类上调用参数化构造函数或调用另一个构造函数可以调用基类构造函数在派生类中。  
  
 **错误 ID:** BC30148  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   调用`MyBase.New`提供所需的参数，或调用此类调用对等构造函数。  
  
     例如，如果基本类具有声明为一个构造函数`Public Sub New(ByVal index as Integer)`中，第一个语句中的派生类构造函数可能是`MyBase.New(100)`。  
  
## <a name="see-also"></a>请参阅

- [继承的基础知识](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
