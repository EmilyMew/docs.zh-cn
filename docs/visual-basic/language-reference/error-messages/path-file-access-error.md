---
title: 路径-文件访问错误
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 3c364296997f571956caad995581102ed990549d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842559"
---
# <a name="pathfile-access-error"></a>路径/文件访问错误
在文件访问权限或磁盘访问操作中，操作系统无法获得的路径和文件名称之间的连接。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  请确保文件规范的格式正确。 文件名称可以包含的完全限定 （绝对） 或相对路径。 完全限定的路径启动驱动器名称 （如果该路径是另一个驱动器上），并列出从根到该文件的显式路径。 任何不是完全限定的路径是相对于当前驱动器和目录。  
  
2.  请确保未尝试保存的文件，将替换现有只读文件。 如果这种情况，更改目标文件的只读属性，或使用其他文件名保存文件。  
  
3.  请确保未尝试打开只读文件中顺序`Output`或`Append`模式。 这种情况，如果打开的文件中`Input`模式或更改文件的只读属性。  
  
4.  请确保未尝试更改数据库或文档中的 Visual Basic 项目。  
  
## <a name="see-also"></a>请参阅

- [错误类型](../../../visual-basic/programming-guide/language-features/error-types.md)
