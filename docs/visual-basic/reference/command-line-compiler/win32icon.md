---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e36e9187ab8c9c2b4950a66ff8ff3fc93adbd9c4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821473"
---
# <a name="-win32icon"></a>-win32icon
在输出文件中插入.ico 文件。 此.ico 文件表示的输出文件中**文件资源管理器**。  
  
## <a name="syntax"></a>语法  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`filename`|要添加到输出文件的.ico 文件。 将文件名括在引号 ("") 如果包含空格。|  
  
## <a name="remarks"></a>备注  
 可以使用 Microsoft Windows 资源编译器 (RC) 创建的.ico 文件。 在编译 Visual c + + 程序; 时会调用资源编译器从.rc 文件创建的.ico 文件。 `-win32icon`和`-win32resource`选项互斥。  
  
 请参阅[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)为引用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]资源文件，或[-资源 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]资源文件。 请参阅[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)导入.res 文件。  
  
|若要设置-win32icon Visual Studio IDE 中|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“应用程序”  选项卡。<br />3.修改中的值**图标**框。|  
  
## <a name="example"></a>示例  
 下面的代码编译`In.vb`并附加.ico 文件， `Rf.ico`。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
