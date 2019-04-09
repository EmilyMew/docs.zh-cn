---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760714"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>允许在类似于 UNC 共享的 URI 中使用 Unicode

|   |   |
|---|---|
|详细信息|在 <xref:System.Uri?displayProperty=fullName> 中，构造包含 UNC 共享名称和 Unicode 字符的文件 URI 将不再导致出现内部状态无效的 URI。 仅当以下各项均为 true 时，该行为才会更改：<ul><li>URI 具有方案 <code>file:</code>，且后接四个及以上的斜杠。</li><li>主机名称以下划线或其他非保留符号开头。</li><li>URI 包含 Unicode 字符。</li></ul>|
|建议|使用始终包含 Unicode 的 URI 的应用程序可能已使用此行为来禁止对 UNC 共享的引用。 这些应用程序应使用 <xref:System.Uri.IsUnc>。|
|范围|边缘|
|版本|4.7.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

