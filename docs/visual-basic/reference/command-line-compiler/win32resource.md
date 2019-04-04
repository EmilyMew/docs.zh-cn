---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 9351e9f6bcb7660dac2c49667ca8db6d578eff7c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834993"
---
# <a name="-win32resource"></a>-win32resource
在输出文件中插入 Win32 资源文件。  
  
## <a name="syntax"></a>语法  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a>自变量  
 `filename`  
 要添加到输出文件的资源文件的名称。 将文件名括在引号 ("") 如果包含空格。  
  
## <a name="remarks"></a>备注  
 您可以创建 Win32 资源文件与 Microsoft Windows 资源编译器 (RC)。  
  
 Win32 资源可以包含版本或位图 （图标） 信息，以帮助标识中的应用程序**文件资源管理器**。 如果未指定`-win32resource`，编译器将生成基于程序集版本的版本信息。 `-win32resource`和`-win32icon`选项互斥。  
  
 请参阅[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)为引用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]资源文件，或[-资源 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]资源文件。  
  
> [!NOTE]
>  `-win32resource`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译`In.vb`并附加 Win32 资源文件， `Rf.res`:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
