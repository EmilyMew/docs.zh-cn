---
title: 应用程序设置体系结构
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: f686fa00662ad29323c1883c45ed0e790b133f2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099776"
---
# <a name="application-settings-architecture"></a>应用程序设置体系结构
本主题介绍应用程序设置体系结构的工作原理，并探讨了体系结构的高级功能，如分组设置和设置键。  
  
 应用程序设置体系结构支持定义应用程序或用户范围的强类型设置，并支持保留应用程序会话间的设置。 该体系结构提供一个默认的持久性引擎，用于将设置保存到本地文件系统以及从本地文件系统加载设置。 该体系结构还定义了用于提供自定义持久性引擎的接口。  
  
 在应用程序中托管自定义组件时，利用提供的接口可使这些自定义组件保留其自己的设置。 通过使用设置键，组件能够保持分隔组件多个实例的设置。  
  
## <a name="defining-settings"></a>定义设置  
 应用程序设置体系结构用于 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 Windows 窗体中，它包含许多在这两种环境中共享的基类。 最重要的是<xref:System.Configuration.SettingsBase>，它提供对一个集合，通过设置访问并提供用于加载和保存设置的低级别方法。 每个环境都实现其自己的类派生自<xref:System.Configuration.SettingsBase>为该环境提供其他设置功能。 在基于 Windows 窗体的应用程序，必须派生自的类上定义所有应用程序设置<xref:System.Configuration.ApplicationSettingsBase>类，该类向基的类添加了以下功能：  
  
-   高层加载和保存操作  
  
-   对用户范围设置的支持  
  
-   将用户的设置还原为预定义的默认值  
  
-   从以前的应用程序版本升级设置  
  
-   在更改设置前或在保存设置前验证设置  
  
 可以使用多个属性定义中所述设置<xref:System.Configuration>命名空间; 中介绍了这些[应用程序设置特性](application-settings-attributes.md)。 在定义一个设置时，必须将其应用与<xref:System.Configuration.ApplicationScopedSettingAttribute>或<xref:System.Configuration.UserScopedSettingAttribute>，它描述了该设置将应用到整个应用程序或只是当前用户。  
  
 以下代码示例定义一个具有单个设置 `BackgroundColor` 的自定义设置类。  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>设置持久性  
 <xref:System.Configuration.ApplicationSettingsBase>类不本身持久保存或加载设置; 此作业由设置提供程序，派生的类<xref:System.Configuration.SettingsProvider>。 如果派生的类<xref:System.Configuration.ApplicationSettingsBase>未指定设置提供程序通过<xref:System.Configuration.SettingsProviderAttribute>，则默认的提供程序， <xref:System.Configuration.LocalFileSettingsProvider>，使用。  
  
 最初随 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 一起发布的配置系统支持通过本地计算机的 machine.config 文件，或在与应用程序一起部署的 `app.`exe.config 文件内提供静态应用程序配置数据。 <xref:System.Configuration.LocalFileSettingsProvider>类按以下方式扩展此本机支持：  
  
-   应用程序范围设置可存储在 machine.config 或 `app.`exe.config 文件中。 Machine.config 始终为只读，而出于安全考虑，`app`.exe.config 对大多数应用程序也限制为只读。  
  
-   用户范围设置可存储在 `app`.exe.config 文件中，在这种情况下，这些设置被视为静态默认设置。  
  
-   非默认的用户范围设置存储在新文件 *user*.config 中，其中 *user* 是当前执行应用程序的用户的用户名。 可以指定的用户范围设置的默认值<xref:System.Configuration.DefaultSettingValueAttribute>。 由于用户范围设置在应用程序执行期间经常更改，因此 `user`.config 始终可读/写。  
  
 所有这 3 种配置文件都以 XML 格式存储设置。 应用程序范围设置的顶级 XML 元素为 `<appSettings>`，而 `<userSettings>` 用于用户范围设置。 同时包含应用程序范围设置和用户范围设置默认值的 `app`.exe.config 文件如下所示：  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
 若要了解配置文件的应用程序设置部分内的元素定义，请参阅[应用程序设置架构](../../configure-apps/file-schema/application-settings-schema.md)。  
  
### <a name="settings-bindings"></a>设置绑定  
 应用程序设置使用 Windows 窗体数据绑定体系结构，提供设置对象和组件间设置更新的双向通信。 如果使用 Visual Studio 创建应用程序设置并将其分配给组件属性，则会自动生成这些绑定。  
  
 您可以仅将应用程序设置绑定到支持的组件<xref:System.Windows.Forms.IBindableComponent>接口。 此外，该组件必须实现的更改事件，特定绑定属性，或通知应用程序设置的属性已更改通过<xref:System.ComponentModel.INotifyPropertyChanged>接口。 如果组件未实现<xref:System.Windows.Forms.IBindableComponent>和要通过 Visual Studio 绑定、 绑定的属性将设置第一次，但不是会更新。 如果组件实现<xref:System.Windows.Forms.IBindableComponent>但不会不支持属性更改通知，当属性更改时，该绑定不会更新设置文件中。  
  
 某些 Windows 窗体组件，如<xref:System.Windows.Forms.ToolStripItem>，不支持设置绑定。  
  
### <a name="settings-serialization"></a>设置序列化  
 当<xref:System.Configuration.LocalFileSettingsProvider>必须将设置保存到磁盘，它将执行以下操作：  
  
1.  使用反射来检查的所有属性上定义你<xref:System.Configuration.ApplicationSettingsBase>派生的类，找出应用了<xref:System.Configuration.ApplicationScopedSettingAttribute>或<xref:System.Configuration.UserScopedSettingAttribute>。  
  
2.  将属性序列化到磁盘。 它首先尝试调用<xref:System.ComponentModel.TypeConverter.ConvertToString%2A>或<xref:System.ComponentModel.TypeConverter.ConvertFromString%2A>上类型的关联<xref:System.ComponentModel.TypeConverter>。 如果不成功，则改用 XML 序列化。  
  
3.  基于设置的特性，确定设置应保存到的文件。  
  
 如果您实现您自己设置的类，则可以使用<xref:System.Configuration.SettingsSerializeAsAttribute>来标记二进制或自定义序列化使用的设置<xref:System.Configuration.SettingsSerializeAs>枚举。 在代码中创建您自己设置的类的详细信息，请参阅[如何：创建应用程序设置](how-to-create-application-settings.md)。  
  
### <a name="settings-file-locations"></a>设置文件位置  
 `app`.exe.config 和 *user*.config 文件的位置因应用程序的安装方式而异。 对于基于 Windows 窗体的应用程序复制到本地计算机上`app`。 exe.config 将驻留在与应用程序的主可执行文件的基目录相同的目录中和*用户*.config 驻留在指定的位置<xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType>属性。 对于通过 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 安装的应用程序，这两个文件都驻留在 %InstallRoot%\Documents and Settings\\*username*\Local Settings 下的 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 数据目录中。  
  
 如果用户启用了漫游配置文件，则这些文件的存储位置稍有不同，漫游配置文件可使用户在域内使用其他计算机时定义不同的 Windows 和应用程序设置。 在这种情况下，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 应用程序和非 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 应用程序的 `app`.exe.config 和 *user*.config 文件均存储在 %InstallRoot%\Documents and Settings\\*username*\Application Data 下。  
  
 若要深入了解应用程序设置功能如何与新部署技术协同使用，请参阅 [ClickOnce 和应用程序设置](/visualstudio/deployment/clickonce-and-application-settings)。 有关 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 数据目录的详细信息，请参阅[在 ClickOnce 应用程序中访问本地数据和远程数据](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)。  
  
## <a name="application-settings-and-security"></a>应用程序设置和安全  
 应用程序设置设计为在部分信任的受限环境中运行，该环境是通过 Internet 或 Intranet 托管的 Windows 窗体应用程序的默认环境。 通过默认设置提供程序使用应用程序设置时，不需要超出部分信任之外的特殊权限。  
  
 在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 应用程序中使用应用程序设置时，`user`.config 文件存储在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 数据目录中。 应用程序的 `user`.config文件大小不能超过由 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 设置的数据目录配额。 有关详细信息，请参阅 [ClickOnce 和应用程序设置](/visualstudio/deployment/clickonce-and-application-settings)。  
  
## <a name="custom-settings-providers"></a>自定义设置提供程序  
 在应用程序设置体系结构中，存在只是松散耦合之间的应用程序设置包装类，派生自<xref:System.Configuration.ApplicationSettingsBase>，并且关联的设置提供程序或提供程序，派生自<xref:System.Configuration.SettingsProvider>。 这种关联定义仅可由<xref:System.Configuration.SettingsProviderAttribute>应用于包装器类或其各个属性。 如果指定的提供程序不是显式设置，默认的提供程序， <xref:System.Configuration.LocalFileSettingsProvider>，使用。 因此，此体系结构支持创建和使用自定义设置提供程序。  
  
 例如，假定要开发和使用提供程序 `SqlSettingsProvider`，它将所有设置数据存储在 Microsoft SQL Server 数据库中。 你<xref:System.Configuration.SettingsProvider>的派生的类会收到此信息在其`Initialize`类型的参数的方法<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>。 然后，可实现<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>方法来从数据存储检索你的设置和<xref:System.Configuration.SettingsProvider.SetPropertyValues%2A>以进行保存。 可以使用您的提供商<xref:System.Configuration.SettingsPropertyCollection>提供给<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>若要确定该属性的名称、 类型和作用域，以及任何其他设置属性，定义该属性。  
  
 提供程序需要实现一个属性和一个方法，这些实现可能不太明显。 <xref:System.Configuration.SettingsProvider.ApplicationName%2A>属性是抽象的属性<xref:System.Configuration.SettingsProvider>; 应将它返回以下程序：  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 派生类还必须实现一个 `Initialize` 方法，该方法既不采用参数也不返回值。 此方法不由<xref:System.Configuration.SettingsProvider>。  
  
 最后，实现<xref:System.Configuration.IApplicationSettingsProvider>刷新设置为提供支持对提供程序，将设置还原为其默认值，并设置从一个应用程序版本升级到另一个。  
  
 实现并编译了提供程序后，需要指示设置类使用此提供程序，而不是使用默认的提供程序。 完成此通过<xref:System.Configuration.SettingsProviderAttribute>。 如果应用于整个设置类，该类定义; 每个设置为使用的提供程序如果应用于各项设置，应用程序设置体系结构为这些设置，使用该提供程序，并使用<xref:System.Configuration.LocalFileSettingsProvider>其余部分。 以下代码示例说明如何指示设置类使用自定义提供程序。  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 提供程序可能会同时从多个线程调用，但其始终会写入同一存储位置；因此，应用程序设置体系结构在任何时候都仅实例化提供程序类的单个实例。  
  
> [!IMPORTANT]
>  应确保提供程序是线程安全的，并且一次只允许一个线程写入配置文件。  
  
 您的提供程序不需要支持所有特性中定义的设置<xref:System.Configuration?displayProperty=nameWithType>命名空间，但它必须在最低支持<xref:System.Configuration.ApplicationScopedSettingAttribute>并<xref:System.Configuration.UserScopedSettingAttribute>，此外还应支持<xref:System.Configuration.DefaultSettingValueAttribute>。 对于其不支持的特性，提供程序应直接失败，而不另行通知；提供程序不应引发异常。 如果设置类使用无效的特性组合，但是 — 例如，应用<xref:System.Configuration.ApplicationScopedSettingAttribute>和<xref:System.Configuration.UserScopedSettingAttribute>为相同的设置，您的提供程序应引发异常并终止操作。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [应用程序设置概述](application-settings-overview.md)
- [自定义控件的应用程序设置](application-settings-for-custom-controls.md)
- [ClickOnce 和应用程序设置](/visualstudio/deployment/clickonce-and-application-settings)
- [应用程序设置架构](../../configure-apps/file-schema/application-settings-schema.md)
