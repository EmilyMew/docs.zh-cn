---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760407"
---
### <a name="wpf-printing-stack-update"></a>WPF 打印堆栈更新

|   |   |
|---|---|
|详细信息|WPF 打印 API 现在使用 <xref:System.Printing.PrintQueue?displayProperty=name> 调用窗口的打印文档包 API，以支持现已弃用的 XPS 打印 API。 这一更改是基于可维护性考虑的，因此用户和开发者应该都不会看到任何行为或 API 使用变化。 当在 Windows 10 创意者更新中运行时，此新打印堆栈默认情况下处于启用状态。 在旧版 Windows 中，旧打印堆栈将继续像过去一样运行。|
|建议|若要在 Windows 10 创意者更新中使用旧堆栈，请将 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> 注册表项的 <code>UseXpsOMPrinting</code> REG_DWORD 值设置为 <code>1</code>。|
|范围|边缘|
|Version|4.7|
|类型|运行时|

