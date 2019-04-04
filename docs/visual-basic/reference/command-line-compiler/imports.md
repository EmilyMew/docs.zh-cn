---
title: -导入 (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 075eeccc7d80943d2757a97b9a355bbea3ef9d4e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833602"
---
# <a name="-imports-visual-basic"></a>-导入 (Visual Basic)
从指定的程序集导入命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`namespaceList`|必需。 要导入的命名空间的以逗号分隔列表。|  
  
## <a name="remarks"></a>备注  
 `-imports`选项将导入当前的源代码文件或从任何引用的程序集设置中定义的任何命名空间。  
  
 使用指定的命名空间中的成员`-imports`适用于编译中所有源代码文件。 使用[Imports 语句 （.NET Namespace 和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)为单个源代码文件中使用命名空间。  
  
|若要设置/导入 Visual Studio 集成的开发环境中|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“引用”选项卡。<br />3.旁边的框中输入命名空间名称**添加用户导入**按钮。<br />4.单击**添加用户导入**按钮。|  
  
## <a name="example"></a>示例  
 下面的代码编译时`/imports:system.globalization`指定。 如果没有它，成功编译要求任一`Imports System.Globalization`语句是包含源代码文件中，开始时，或作为完全限定属性`System.Globalization.CultureInfo.CurrentCulture.Name`。

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [引用和 Imports 语句](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
