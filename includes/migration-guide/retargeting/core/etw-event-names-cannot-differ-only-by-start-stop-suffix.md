---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760983"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>ETW 事件名称无法仅通过“Start”或“Stop”后缀区别开来

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.6 和 4.6.1 中，当两个 Windows 事件跟踪 (ETW) 事件名称只有 &quot;Start&quot; 或 &quot;Stop&quot; 后缀不同时（例如，当一个事件命名为 <code>LogUser</code>，另一个事件命名为 <code>LogUserStart</code>），运行时会引发 <xref:System.ArgumentException>。 在这种情况下，运行时不会构建不能发出任何日志记录的事件源。|
|建议|若要避免此异常，请确保两个事件名称不是只有 &quot;Start&quot; 或 &quot;Stop&quot; 后缀不同。从 .NET Framework 4.6.2 开始，将删除此要求，运行时可区分只有 &quot;Start&quot; 和 &quot;Stop&quot; 后缀不同的事件名称。|
|范围|边缘|
|版本|4.6|
|类型|重定目标|

