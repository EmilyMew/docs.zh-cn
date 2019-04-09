---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761236"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>当 WPF 窗口超出单个显示屏时，会不经剪辑就呈现该窗口

|   |   |
|---|---|
|详细信息|在 Windows 8 及更高版本上运行的 .NET Framework 4.6 中，当一个窗口超出多监视器方案中的单个显示屏时，会不经剪辑就呈现整个窗口。 这与先前版本的 .NET Framework 不同，以前的版本在 WPF 窗口超出单个显示屏时会剪辑该窗口。|
|建议|可以使用应用程序的配置文件中的 <code>&lt;appSettings&gt;</code> 的 <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 元素，或在应用启动时设置 <code>EnableMultiMonitorDisplayClipping</code> 属性，显式设置此行为（无论剪辑与否）。|
|范围|次要|
|版本|4.6|
|类型|运行时|

