---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760608"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a>现在支持 Unicode 标准版本 8.0 类别

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.6.2 中，Unicode 数据已从 Unicode 标准版本 6.3 升级到版本 8.0。  在 .NET Framework 4.6.2 中请求 Unicode 字符类别时，某些结果可能与以前的 .NET Framework 版本中的结果不匹配。  此更改主要影响切罗基语音节和西双版纳新傣文元音标记和音调标记。|
|建议|检查代码并删除/更改依赖硬编码 Unicode 字符类别的逻辑。|
|范围|次要|
|版本|4.6.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

