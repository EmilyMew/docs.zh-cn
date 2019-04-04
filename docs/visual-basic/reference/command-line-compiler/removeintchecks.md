---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822721"
---
# <a name="-removeintchecks"></a>-removeintchecks
将溢出错误检查对整数运算打开或关闭。  
  
## <a name="syntax"></a>语法  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`+` &#124; `-`|可选。 `-removeintchecks-`选项导致编译器检查所有整数计算中的溢出错误。 默认值为 `-removeintchecks-`。<br /><br /> 指定`-removeintchecks`或`-removeintchecks+`可以防止错误检查，并使整数计算速度更快。 但是，不进行错误检查，如果出现溢出数据类型的容量，可能不会生成错误存储不正确的结果。|  
  
|在 Visual Studio 集成的开发环境中设置-removeintchecks|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“编译”选项卡。<br />3.单击“高级”按钮。<br />4.修改的值**整数溢出检查**框。|  
  
## <a name="example"></a>示例  
 下面的代码编译`Test.vb`和将禁用整数溢出错误检查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
