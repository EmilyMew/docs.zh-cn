---
title: 保护包装代码
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4d8497d17e1a82791f4dd6ca8f91c9a012db167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132777"
---
# <a name="securing-wrapper-code"></a>保护包装代码
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 包装代码，特别是在包装的信任级别比使用它的代码的信任级别更高时，可以打开一组唯一的安全漏洞。 代表调用方完成的任何操作都是被利用的潜在漏洞，其中进行适当安全检查时不包括调用方的有限权限。  
  
 请勿通过包装启用调用方无法自行执行的任何操作。 相对于完整堆栈遍历需求，在进行牵涉到限制安全性检查的操作时，这项操作特别危险。 当涉及到单级别检查时，在实际调用方和正在讨论的 API 元素之间干预包装代码很容易导致本应失败的安全检查成功，从而便削弱了安全性。  
  
## <a name="delegates"></a>委托  
 委托安全性因 .NET Framework 的版本而异。  本节介绍了不同的委托行为和相关的安全注意事项。  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>.NET Framework 1.0 版和 1.1 版  
 .NET Framework 1.0 版和 1.1 版可执行以下针对委托创建者和委托调用方的安全性操作。  
  
-   当创建委托时，将针对委托创建者的权限集执行对委托目标方法的安全链接要求。  未遵循安全操作将导致 <xref:System.Security.SecurityException>。  
  
-   当调用委托时，将执行对委托调用方的任何现有的安全需求。  
  
 无论何时，当代码从可能调用它的不太受信任代码中提取 <xref:System.Delegate> 时，确保不会启用不太受信任代码提升其权限。 如果提取委托想在以后使用，则创建委托的代码不会出现在调用堆栈之上，并且其权限也得不到测试（如果委托中或以下的代码尝试执行受保护操作）。 如果你的代码和调用方的代码其特权比创建者更高，则创建者可以安排调用路径，使其不作为调用堆栈的一部分。  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>在 2.0 及更高版本的.NET Framework  
 与早期版本中，不同版本 2.0 和更高版本的.NET Framework 执行针对委托创建者的安全操作时创建并调用该委托。  
  
-   当创建委托时，将针对委托创建者的权限集执行对委托目标方法的安全链接要求。  未遵循安全操作将导致 <xref:System.Security.SecurityException>。  
  
-   在创建委托期间还会捕获委托创建者的权限集并存储在委托中。  
  
-   待用委托时，如果委托创建者和调用方属于不同的程序集，则将针对当前内容中的任何需求首先评估委托创建者捕获的权限集。  然后才是执行针对委托调用方的现有安全需求。  
  
## <a name="link-demands-and-wrappers"></a>链接需求和包装  
 在安全性基础结构中，已经对链接需求加强了特殊保护，但它依然是代码中潜在的漏洞源。  
  
 如果完全受信任的代码调用属性、 事件或方法受[LinkDemand](../../../docs/framework/misc/link-demands.md)，如果调用成功**LinkDemand**满足权限检查调用方。 此外，如果完全受信任的代码公开一个采用的名称的属性和调用其**获取**访问器使用反射，调用**获取**即使用户代码的作用也会成功访问器不具有访问此属性的权限。 这是因为**LinkDemand**只检查直接调用方，它是完全受信任的代码。 从根本上而言，完全受信任的代码可代表用户代码发出特权调用，而无需确保用户代码是否有权发出该调用。  
  
 若要防止此类安全漏洞，公共语言运行时都会检查扩展为完整堆栈遍历需求对方法、 构造函数、 属性或事件的受保护的任何间接调用**LinkDemand**。 这种保护会带来一些性能损失，并更改安全检查语义；完整的堆栈遍历需求可能会失败，其中会通过速度更快的单一级别检查。  
  
## <a name="assembly-loading-wrappers"></a>加载包装的程序集  
 用于加载托管代码的几种方法，包括 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用调用方的证据加载程序集。 如果包装任何这些方法，安全系统将使用代码的授予权限（而不是使用包装其调用方的权限）加载程序集。 不应使用不太受信任代码加载比包装器调用方的权限更高的代码。  
  
 否则，将会降低任何具有完全信任或比潜在调用方（）的信任程度明显更高的代码的安全性。 如果你的代码有一个公共方法，它接受字节数组，并将其传递给**Assembly.Load**，从而代表调用方创建程序集，它可能会破坏安全性。  
  
 此问题适用于以下 API 元素：  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Demand VS LinkDemand  
 声明性安全提供了两种类型相似但执行方法完全不同的安全检查。 你应该了解这两种形式，因为选择错误可能导安全性降低或性能受损。  
  
 声明性安全提供了下列安全检查：  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand> 指定代码访问安全堆栈审核。 堆栈上的所有调用方必须具有特定权限或标识才能通过。 **需**出现在每次调用，因为堆栈可能包含不同的调用方。 如果重复调用一种方法，则每次都会执行安全检查。 **需**是很好地防范引诱攻击; 将检测到未经授权的代码尝试通过它获取。  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md)发生在实时 (JIT) 编译时和检查仅直接调用方。 这种安全检查不会检查调用方的调用方。 一旦此项检查成功，无论调用方调用的次数为多少，都无需任何其他安全性开销。 但是，这种方法没有对引诱攻击提供保护。 与**LinkDemand**，任何通过的测试，并且可以引用您的代码的代码可以通过允许恶意代码利用已授权的代码进行调用可能会破坏安全性。 因此，不使用**LinkDemand**除非可以彻底避免所有可能的漏洞。  
  
    > [!NOTE]
    >  在中[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，已被取代，链接要求<xref:System.Security.SecurityCriticalAttribute>属性中<xref:System.Security.SecurityRuleSet.Level2>程序集。 <xref:System.Security.SecurityCriticalAttribute>等效于链接要求完全信任; 但是，它还会影响继承规则。 有关此更改的详细信息，请参阅[安全透明的代码，级别 2](../../../docs/framework/misc/security-transparent-code-level-2.md)。  
  
 使用时所需的其他预防措施**LinkDemand**必须单独编程; 安全系统可以帮助执行。 任何错误都会打开安全漏洞。 利用你的代码的所有授权代码都必须负责执行以下操作实现其他安全性：  
  
-   限制调用代码对类或程序集的访问权限。  
  
-   对显示在将被调用的代码上的调用代码施行相同的安全检查并负责让其调用方也执行这种检查。 例如，如果您编写的代码调用方法的方法使用保护**LinkDemand**有关<xref:System.Security.Permissions.SecurityPermission>与<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>指定标志，还应该使您的方法**LinkDemand** （或**需**，这是更强) 执行此权限。 例外情况是如果你的代码将使用**LinkDemand**-您决定以有限方式受保护的方法是安全的在代码中有其他安全保护机制 （例如需求）。 对于这种例外情况，调用方需对削弱基础代码的安全性保护负责。  
  
-   确保你的代码调用方无法欺骗你的代码代表自己调用受保护的代码。 换言之，调用方不能强制授权代码向受保护的代码传递特定参数，或从受保护的代码中得到返回结果。  
  
### <a name="interfaces-and-link-demands"></a>接口和链接需求  
 如果虚方法、 属性或事件**LinkDemand**重写基类方法，基类方法还必须属于同一**LinkDemand**重写方法才能有效。 当然，恶意代码重新强制转换为基类并调用基类方法的这种情况也是有可能的。 另请注意，可以将链接需求以隐式方式添加到不包含 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 程序集级别属性的程序集。  
  
 当接口方法也具有链接需求时，使用链接需求实现保护方法也是不错的选择。 请注意下列有关使用链接需求的接口：  
  
-   如果将置于**LinkDemand**上实现接口方法的类的公共方法**LinkDemand**如果之后强制转换为接口并调用该方法不会强制执行。 在这种情况下，因为针对接口，链接**LinkDemand**的接口上是遵循。  
  
 审阅安全性问题的以下各项：  
  
-   接口方法上的显式链接需求。 确保这些链接需求提供预期保护。 确定恶意代码是否可以使用强制转换来避开链接需求，如前面所述。  
  
-   应用了包含链接需求的虚拟方法。  
  
-   它们实现的类型和接口。 这些应使用相一致的链接需求。  
  
## <a name="see-also"></a>请参阅

- [代码安全维护指南](../../../docs/standard/security/secure-coding-guidelines.md)
