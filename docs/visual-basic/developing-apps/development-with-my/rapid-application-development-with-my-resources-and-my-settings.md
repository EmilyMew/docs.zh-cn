---
title: 使用 My.Resources 和 My.Settings 快速开发应用程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 4a9021af23200323397cc49fa1a44a0cc48b5a1d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816702"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>使用 My.Resources 和 My.Settings 快速开发应用程序 (Visual Basic)
`My.Resources`对象提供了对应用程序的资源的访问，并可动态检索应用程序的资源。  
  
## <a name="retrieving-resources"></a>检索资源  
 可以通过检索大量的资源，例如音频文件、 图标、 图像和字符串`My.Resources`对象。 例如，可以访问应用程序的特定于区域性的资源文件。 下面的示例设置窗体的图标的图标名为`Form1Icon`存储在应用程序的资源文件。  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`对象公开只有全局资源。 它不提供对与窗体相关联的资源文件的访问。 必须从窗体来访问窗体资源。  
  
 同样，`My.Settings`对象提供对应用程序的设置的访问，并允许您动态存储和检索属性设置，并且你的应用程序的其他信息。 有关详细信息，请参阅[My.Resources 对象](../../../visual-basic/language-reference/objects/my-resources-object.md)并[My.Settings 对象](../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## <a name="see-also"></a>请参阅

- [My.Resources 对象](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [My.Settings 对象](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [访问应用程序设置](../../../visual-basic/developing-apps/programming/app-settings/index.md)
