---
title: 代码访问安全策略兼容性和迁移
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d9281e52de43391a92262f85084715ccabd5515
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364770"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>代码访问安全策略兼容性和迁移

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

代码访问安全性 (CAS) 的策略部分在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中已过时。 因此，您可能会遇到编译警告和运行时异常如果调用过时的策略类型和成员[显式](#explicit_use)或[隐式](#implicit_use)（通过其他类型和成员）。

可以通过以下任一方法来避免这些警告和错误：

- [迁移](#migration)到[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]替换已过时的调用。

   \- 或 -

- 使用[< NetFx40_LegacySecurityPolicy > 配置元素](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)来选择启用旧版 CAS 策略行为。

本主题包含以下各节：

- [显式使用](#explicit_use)

- [隐式使用](#implicit_use)

- [错误和警告](#errors_and_warnings)

- [迁移：替换为已过时的调用的](#migration)

- [兼容性：使用 CAS 策略旧版选项](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>显式使用

直接操作安全策略或需要沙盒的 CAS 策略的成员已过时，并且默认情况下将产生错误。

这方面的示例如下：

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>隐式使用

由于若干程序集加载重载隐式使用 CAS 策略，因此它们产生错误。 这些重载采用用于解决 CAS 策略的 <xref:System.Security.Policy.Evidence> 参数，并为程序集提供权限授予集。

以下是一些示例。 过时的重载是使用 <xref:System.Security.Policy.Evidence> 作为参数的重载：

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>错误和警告

当使用过时的类型和成员时，会产生下列错误消息。 请注意，<xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 类型本身并未过时。

编译时警告：

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

运行时异常：

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>迁移：替换为已过时的调用的

### <a name="determining-an-assemblys-trust-level"></a>确定程序集的信任级别

CAS 策略通常用于确定程序集或应用程序域的权限授予集或信任级别。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 公开以下无需解析安全策略的有用属性：

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>应用程序域沙盒

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> 方法通常用于对应用程序域中的程序集进行沙盒处理。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]公开不需要使用的成员<xref:System.Security.Policy.PolicyLevel>实现此目的。 有关详细信息，请参阅[如何：运行沙盒中部分受信任的代码](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中所述。

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>确定部分受信任的代码的“安全”或“合理”权限集

主机通常需要确定适用于沙盒处理托管代码的权限。 之前[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，CAS 策略提供某种方式来这样做的<xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>方法。 作为替代，[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]提供了<xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType>方法，它将返回一个安全且标准的权限集为提供的证据。

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>非沙盒处理方案：对程序集加载重载

使用程序集加载重载的原因可能是为了使用不可通过其他方式使用的参数，而不是对程序集进行沙盒处理。 从开始[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，不需要的程序集加载重载<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>对象作为参数，例如， <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>，启用此方案。

如果要对程序集进行沙盒处理，请使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 重载。

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>兼容性：使用 CAS 策略旧版选项

[< NetFx40_LegacySecurityPolicy > 配置元素](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)，可以指定进程或库使用旧版 CAS 策略。 启用此元素时，策略和证据重载将与其在 Framework 以前版本中进行的操作相同。

> [!NOTE]
> CAS 策略行为是在运行时版本的基础上指定的，因此修改一个运行时版本的 CAS 策略不会影响另一个版本的 CAS 策略。

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>请参阅

- [如何：运行沙盒中部分受信任的代码](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [安全编码准则](../../standard/security/secure-coding-guidelines.md)
