---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 0550e4ad700494c8773a5d9b5b282dfa116adfed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813361"
---
# <a name="-baseaddress"></a>-baseaddress
创建 DLL 时，请指定默认基址。  
  
## <a name="syntax"></a>语法  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`address`|必需。 DLL 的基址。 此地址必须指定为十六进制数。|  
  
## <a name="remarks"></a>备注  
 设置 DLL 的默认基址[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。  
  
 请注意，此地址中的低序字将被舍入。 例如，如果指定 0x11110001，它是舍入为 0x11110000。  
  
 若要完成 DLL 的签名过程，使用`–R`Strong Naming 工具 (Sn.exe) 选项。  
  
 如果目标不是一个 DLL，则忽略此选项。  
  
|若要在 Visual Studio IDE 中设置-baseaddress|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“编译”选项卡。<br />3.单击 **“高级”**。<br />4.修改中的值**DLL 基址：** 框。 **注意：**     **DLL 基址：** 框是只读的除非目标是一个 DLL。|  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn.exe （强名称工具）](../../../framework/tools/sn-exe-strong-name-tool.md))
