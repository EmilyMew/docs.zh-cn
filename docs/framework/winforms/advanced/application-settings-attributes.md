---
title: 应用程序设置特性
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: f945d8e6918c271eeb5fdf3cf9c357b1c2bbca66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079638"
---
# <a name="application-settings-attributes"></a>应用程序设置特性
应用程序设置体系结构提供可应用到应用程序设置包装类或其各个属性的多个属性。 这些属性将检查在运行时由应用程序设置基础结构通常专门设置提供程序，以便使其正常运行的自定义包装器所述的需求。  
  
 下表列出了可以应用于应用程序设置包装类，此类的各个属性，或两者的属性。 根据定义，只有单个作用域属性 —**UserScopedSettingAttribute**或**ApplicationScopedSettingAttribute**— 必须应用于每个设置属性。  
  
> [!NOTE]
>  自定义设置提供程序，派生自<xref:System.Configuration.SettingsProvider>类中，只需识别以下三个属性：**ApplicationScopedSettingAttribute**， **UserScopedSettingAttribute**，和**DefaultSettingValueAttribute**。  
  
|特性|Target|描述|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|双向|指定要用于持久性的设置提供程序的短名称。<br /><br /> 如果未提供此属性，默认的提供程序， <xref:System.Configuration.LocalFileSettingsProvider>，假定。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|双向|将属性定义为用户范围的应用程序设置。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|双向|将属性定义为应用程序范围的应用程序设置。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|属性|指定可以反序列化提供程序到此属性的硬编码默认值的字符串。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>不需要此属性，并提供此属性是否存在已保留某个值将重写的任何值。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|属性|提供单个设置，主要由运行时和设计时工具的描述性的测试。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|类|提供的设置组的显式名称。 如果此属性缺失，<xref:System.Configuration.ApplicationSettingsBase>使用包装类的名称。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|类|有关设置组中，主要由运行时和设计时工具提供描述性的测试。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|双向|指定应提供给设置组或属性的零个或多个可管理性服务。 可用的服务由描述<xref:System.Configuration.SettingsManageability>枚举。|  
|<xref:System.Configuration.SpecialSettingAttribute>|属性|指示设置属于一个特殊的预定义的类别，如连接字符串，它建议通过设置提供程序的特殊处理。 此属性将预定义的类别定义由<xref:System.Configuration.SpecialSetting>枚举。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|双向|指定的设置组或属性的首选序列化机制。 定义可序列化机制<xref:System.Configuration.SettingsSerializeAs>枚举。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|属性|指定设置提供程序，应禁用所有的应用程序升级功能的标记属性。|  
  
 *类*指示特性可以应用到应用程序设置包装器类。 *属性*指示该属性可以应用到仅设置属性。 *同时*指示该特性可以应用到任何一级。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [应用程序设置体系结构](application-settings-architecture.md)
- [如何：创建应用程序设置](how-to-create-application-settings.md)
