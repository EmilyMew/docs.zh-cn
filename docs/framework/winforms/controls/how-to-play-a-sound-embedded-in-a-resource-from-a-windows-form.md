---
title: 如何：从 Windows 窗体播放资源中嵌入的声音
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078572"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>如何：从 Windows 窗体播放资源中嵌入的声音
可以使用<xref:System.Media.SoundPlayer>类播放嵌入的资源中的声音。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
 导入<xref:System.Media?displayProperty=nameWithType>命名空间。  
  
 将声音文件作为嵌入资源包括在项目中。  
  
 将“\<程序集名称>”替换为嵌入声音文件的程序集的名称。 不要包含“.dll”后缀。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Media.SoundPlayer>
- [如何：从 Windows 窗体播放声音](how-to-play-a-sound-from-a-windows-form.md)
- [如何：在 Windows 窗体上循环播放声音](how-to-loop-a-sound-playing-on-a-windows-form.md)
