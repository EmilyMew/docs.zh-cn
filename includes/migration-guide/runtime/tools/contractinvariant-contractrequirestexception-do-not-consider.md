---
ms.openlocfilehash: 91e09e71a32bb6d410ff52a97a8d14384ee3a5f1
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58467062"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant 或 Contract.Requires\<TException> 不认为 String.IsNullOrEmpty 为 pure

|   |   |
|---|---|
|详细信息|对于面向 .NET Framework 4.6.1 的应用，如果 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 的不变协定或 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> 的前提条件协定调用 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，则重写器会发出编译器警告 CC1036：&quot; 在方法中没有 [Pure] 的情况下检测到对方法 <xref:System.String.IsNullOrWhiteSpace%2A?displayProperty=nameWithType> 的调用。&quot;这是编译器警告，不是编译器错误。|
|建议|此行为在 [GitHub 问题 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已得到解决。 要去除此警告，可以从 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下载并编译代码协定工具的已更新版本的源代码。 可在页面底部找到下载信息。|
|范围|次要|
|版本|4.6.1|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

