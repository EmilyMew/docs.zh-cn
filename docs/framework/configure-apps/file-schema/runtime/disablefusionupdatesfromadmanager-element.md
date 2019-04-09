---
title: <disableFusionUpdatesFromADManager> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27c8c1cac68aca1c40826ff549d62d9636d9b0c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085878"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > 元素
指定是否禁用允许运行时主机为应用程序域重写配置设置的默认行为。  
  
 \<配置 > 元素  
\<运行时 > 元素  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>语法  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|enabled|必需的特性。<br /><br /> 指定是否禁用重写合成设置的默认功能。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|“值”|Description|  
|-----------|-----------------|  
|0|不要禁用重写合成设置的功能。 这是默认行为，从开始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。|  
|1|禁用重写合成设置的功能。 这将恢复为.NET Framework 的早期版本的行为。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 从开始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，默认行为是允许<xref:System.AppDomainManager>对象重写配置设置，通过使用<xref:System.AppDomainSetup.ConfigurationFile%2A>属性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法<xref:System.AppDomainSetup>对象传递给您的实现<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>的子类中的方法， <xref:System.AppDomainManager>。 对于默认应用程序域，您更改的设置重写应用程序配置文件指定的设置。 对于其他应用程序域，这些重写的配置设置，已将传递给<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。  
  
 可以传递新的配置信息，也可以传递 null (`Nothing`在 Visual Basic 中) 以消除中传递的配置信息。  
  
 未将配置信息传递给<xref:System.AppDomainSetup.ConfigurationFile%2A>属性和<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法。 如果将配置信息传递给时，信息传递给<xref:System.AppDomainSetup.ConfigurationFile%2A>属性被忽略，因为<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法重写应用程序配置文件中的配置信息。 如果您使用<xref:System.AppDomainSetup.ConfigurationFile%2A>属性，您可以将传递 null (`Nothing`在 Visual Basic 中) 到<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法来消除对的调用中指定的任何配置字节<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。  
  
 除了配置信息，可以更改以下设置，在<xref:System.AppDomainSetup>传递给您的实现的对象<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法： <xref:System.AppDomainSetup.ApplicationBase%2A>， <xref:System.AppDomainSetup.ApplicationName%2A>， <xref:System.AppDomainSetup.CachePath%2A>， <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>， <xref:System.AppDomainSetup.DisallowBindingRedirects%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A>， <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>， <xref:System.AppDomainSetup.DynamicBase%2A>， <xref:System.AppDomainSetup.LoaderOptimization%2A>， <xref:System.AppDomainSetup.PrivateBinPath%2A>， <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>， <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>，和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。  
  
 作为一种方式使用`<disableFusionUpdatesFromADManager>`元素中，您可以禁用默认行为通过创建注册表设置或通过设置环境变量。 在注册表中，创建一个名为`COMPLUS_disableFusionUpdatesFromADManager`下`HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`，并将值设置为 1。 在命令行设置环境变量`COMPLUS_disableFusionUpdatesFromADManager`为 1。  
  
## <a name="example"></a>示例  
 下面的示例演示如何禁止重写通过使用合成设置`<disableFusionUpdatesFromADManager>`元素。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [运行时如何定位程序集](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
