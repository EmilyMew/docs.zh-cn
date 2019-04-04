---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: ccf569aea1363d256728e122818b70284a9e250d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830365"
---
# <a name="-delaysign"></a>-delaysign
指定程序集是完全签名的还是部分签名的。  
  
## <a name="syntax"></a>语法  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>自变量  
 `+` &#124; `-`  
 可选。 如果需要完全签名的程序集，则使用 `-delaysign-`。 使用`-delaysign+`如果想要将公钥放在有符号哈希的程序集和保留空间中。 默认值为 `-delaysign-`。  
  
## <a name="remarks"></a>备注  
 `-delaysign`选项没有任何影响，除非用于[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。  
  
 在请求完全签名的程序集时，编译器会对包含清单（程序集元数据）的文件进行哈希处理，并使用私钥对哈希进行签名。 产生的数字签名存储在包含清单的文件中。 程序集延迟签名时，编译器不会计算和存储文件中的签名，但预留空间，以便可以稍后添加该签名。  
  
 例如，通过使用`-delaysign+`，在组织中的开发人员可以分发测试人员可注册到全局程序集缓存和使用程序集的无符号的测试版本。 在完成工作的程序集时，负责组织的私钥的人员完全可以登录该程序集。 这种划分可防止组织的专用密钥泄露，同时允许所有开发人员若要运行的程序集。  
  
 请参阅[创建和使用具有强名称程序集](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)有关为程序集签名的详细信息。  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>在 Visual Studio 集成的开发环境中设置-delaysign  
  
1.  在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。   
  
2.  单击“签名”选项卡。  
  
3.  中的值设置**仅延迟签名**框。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
