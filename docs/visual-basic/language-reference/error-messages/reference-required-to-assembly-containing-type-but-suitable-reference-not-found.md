---
title: 需要引用包含类型“<assemblyidentity>”的程序集“<typename>”，但由于项目“<projectname1>”和“<projectname2>”之间存在二义性，未能找到合适的引用
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 3cfdf8150c8ccd9e1b4f047cd1ce8ee4ad6bbc1a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813400"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>需要对程序集的引用\<assemblyidentity > 包含类型\<类型名称 >，但由于项目之间存在多义性。 找不到合适的引用\<projectname1 > 和\<项目名称 2> >
表达式使用在项目外部定义的类型，如类、结构、接口、枚举或委托。 但是，你具有对定义该类型的多个程序集的项目引用。  
  
 引用的项目会生成名称相同的程序集。 因此，编译器无法确定对要访问的类型使用哪一个程序集。  
  
 若要访问另一个程序集中定义的类型，Visual Basic 编译器必须具有对该程序集的引用。 此引用必须单一、明确，不会导致项目之间循环引用。  
  
 **错误 ID:** BC30969  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  确定产生最佳程序集引用的项目。 为便于确定，你可以使用文件访问轻松程度和更新频率等条件。  
  
2.  在项目属性中，添加对包含某程序集的文件的引用，该程序集定义正在使用的类型。  
  
## <a name="see-also"></a>请参阅

- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
- [对已声明元素的引用](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
- [有关无效的引用的疑难解答](/visualstudio/ide/troubleshooting-broken-references)
