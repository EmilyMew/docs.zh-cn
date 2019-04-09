---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760415"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>在某些情况下工作流现在引发原始异常，而不是 NullReferenceException

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.6.2 和更低版本中，当工作流活动的 Execute 方法引发 <xref:System.Exception.Message> 属性 <code>null</code> 值的异常，那么 System.Activities 工作流运行时引发 <xref:System.NullReferenceException?displayProperty=name> 掩码原始异常。在 .NET Framework 4.7 中，引发之前掩码的异常。|
|建议|如果你的代码依赖于处理 <xref:System.NullReferenceException?displayProperty=name>，请将其更改为捕获自定义活动可能引发的异常。|
|范围|次要|
|版本|4.7|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

