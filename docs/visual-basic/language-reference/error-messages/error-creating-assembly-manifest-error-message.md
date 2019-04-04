---
title: 创建程序集清单时出错：<error message>
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: f9d7867157b65d746809d9b2f50797285d7fcd9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831952"
---
# <a name="error-creating-assembly-manifest-error-message"></a>创建程序集清单时出错：\<错误消息 >
Visual Basic 编译器调用程序集链接器 (Al.exe，也称作 Alink) 生成包含清单的程序集。 该链接器已报告在创建程序集的预发出阶段中出错。  
  
 如果指定的密钥文件或密钥容器有问题，就可能发生错误。 若要对程序集进行完全签名，必须提供包含公钥和私钥信息的有效密钥文件。 若要延迟对程序集的签名，必须选择“仅延迟签名”复选框，并提供包含公钥信息的有效密钥文件。 当程序集为延迟签名时，不需要使用私有密钥。 有关详细信息，请参阅[如何：使用强名称为程序集签名](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
 **错误 ID:** BC30140  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查引用的错误信息并参考主题[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。 有关错误 AL1019 的进一步解释和建议  
  
2.  如果仍然出现错误，则收集有关该情况的信息并通知 Microsoft 产品支持服务。  
  
## <a name="see-also"></a>请参阅

- [如何：使用强名称为程序集签名](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [“项目设计器”->“签名”页](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [与我们交流](/visualstudio/ide/talk-to-us)
