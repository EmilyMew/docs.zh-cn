---
title: 危险权限和策略管理
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae24cdcb97e30da0bd4aec6569ef3dcda11488c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078937"
---
# <a name="dangerous-permissions-and-policy-administration"></a>危险权限和策略管理
.NET Framework 为其提供权限的多个受保护的操作可能允许绕过安全系统。 应仅对可信的代码，并且仅在必要的时候授予这些危险的权限。 如果它被授予这些权限，通常会对恶意代码没有任何防范。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，已对 .NET Framework 安全模型和术语作出重要更改。 有关这些更改的详细信息，请参阅[安全更改](../../../docs/framework/security/security-changes.md)。  
  
 下表介绍了危险权限。  
  
|权限|潜在的风险|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|允许托管代码调用到非托管代码中，常常是很危险的。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|如果没有验证，代码可以执行任何操作。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|无效证据可以欺骗安全策略。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|修改安全策略的功能可以禁用安全性。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|序列化的使用可以避开可访问性机制。 有关详细信息，请参阅 [安全和序列化](../../../docs/framework/misc/security-and-serialization.md)。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|设置当前主体的功能可以欺骗基于角色的安全性。|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|由于与线程关联的安全状态，因此对线程进行操作很危险。|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|可以使用私有成员来攻克可访问性机制。|  
  
## <a name="see-also"></a>请参阅

- [代码安全维护指南](../../../docs/standard/security/secure-coding-guidelines.md)
