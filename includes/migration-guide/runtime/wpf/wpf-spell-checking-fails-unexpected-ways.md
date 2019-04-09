---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761269"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF 拼写检查以一种意想不到的方式失败

|   |   |
|---|---|
|详细信息|这包括 WPF 拼写检查器的诸多问题：<ul><li>WPF 拼写检查器有时会引发 <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>当使用“以不同用户身份运行”启动应用程序时，WPF 拼写检查器会无法使用 <xref:System.UnauthorizedAccessException></li><li>WPF 拼写检查器在组合词（如德语中的“Hausnummer”）中错误地标出了拼写错误。</li></ul>|
|建议|问题 #1 - 此问题已在 .NET Framework 4.6.2 中解决 问题 #2 - 当使用“以不同用户身份运行”启动应用程序时，不再支持 WPF 拼写检查器。 从 .NET Framework 4.6.2 开始，以此方式启动的应用程序将不再意外出现故障 - 而是静默禁用 WPF 拼写检查器。 问题 #3 - 此问题已在 .NET Framework 4.6.2 中解决。|
|范围|边缘|
|版本|4.6.1|
|类型|运行时|

