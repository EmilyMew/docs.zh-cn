---
ms.openlocfilehash: 38dd0b33202b8e8f1708ebec689333bd5367c93f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760609"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>更改 TextBlock 控件父级的 IsEnabled 属性会影响任何子控件

|   |   |
|---|---|
|详细信息|自 .NET Framework 4.6.2 起，更改 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控件父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 属性会影响 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控件的任意子控件（例如超链接和按钮）。在 .NET Framework 4.6.1 和更早版本中，<xref:System.Windows.Controls.TextBlock?displayProperty=name> 中的控件并非始终反映 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> 属性状态。|
|建议|无。 此更改符合 <xref:System.Windows.Controls.TextBlock?displayProperty=name> 控件中各控件的预期行为。|
|范围|次要|
|版本|4.6.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

