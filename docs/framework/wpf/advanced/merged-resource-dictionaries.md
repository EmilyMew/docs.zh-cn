---
title: 合并资源字典
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 17dd8e0c02d71fc7e72800fc578866188d03060e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097234"
---
# <a name="merged-resource-dictionaries"></a>合并资源字典
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 资源支持合并的资源字典功能。 此功能提供一种方法，可在编译的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 应用程序外部定义 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序的资源部分。 然后可以在应用程序之间共享资源，还可更方便地将资源隔离以进行本地化。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>引入合并资源字典  
 在标记中，使用以下语法将合并资源字典引入页面：  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 请注意，<xref:System.Windows.ResourceDictionary>元素不具有[X:key 指令](../../xaml-services/x-key-directive.md)，通常需要的资源集合中的所有项。 但另一个<xref:System.Windows.ResourceDictionary>中引用<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合是一种特殊情况，保留此合并的资源字典方案。 <xref:System.Windows.ResourceDictionary>引入了合并资源字典不能有[X:key 指令](../../xaml-services/x-key-directive.md)。 通常情况下，每个<xref:System.Windows.ResourceDictionary>内<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合指定<xref:System.Windows.ResourceDictionary.Source%2A>属性。 值<xref:System.Windows.ResourceDictionary.Source%2A>应为[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]解析到要合并的资源文件的位置。 目标[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]必须是另一个[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件中，使用<xref:System.Windows.ResourceDictionary>作为其根元素。  
  
> [!NOTE]
>  它是合法定义中的资源<xref:System.Windows.ResourceDictionary>作为指定的替代方法指定为合并字典<xref:System.Windows.ResourceDictionary.Source%2A>，或除了任何资源都包含从指定的源。 但是，这不是一种常见方案；合并字典的主要方案是从外部文件位置合并资源。 如果你想要指定页的标记中的资源，则应通常定义这些主<xref:System.Windows.ResourceDictionary>而不是在合并的字典。  
  
## <a name="merged-dictionary-behavior"></a>合并字典的行为  
 合并字典中的资源占用资源查找范围中的一个位置，此范围恰好在它们合并到的主要资源字典中的范围之后。 尽管任何字典中的资源键必须唯一，但一个资源键可在一组合并字典中多次存在。 在这种情况下，返回的资源将来自按顺序在找到的最后一个字典<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合。 如果<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合中定义[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，则合并的字典集合中的顺序是提供在标记中元素的顺序。 如果在主要字典和合并的字典中均定义了同一个键，则返回的资源将来自主要字典。 这些范围规则同等地适用于静态资源引用和动态资源引用。  
  
### <a name="merged-dictionaries-and-code"></a>合并字典和代码  
 可通过代码将合并字典添加到 `Resources` 字典。 默认情况下，最初为空<xref:System.Windows.ResourceDictionary>存在于任何`Resources`属性都具有默认值，最初为空<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合属性。 若要添加的代码通过合并的字典，则获取到所需的主副本的引用<xref:System.Windows.ResourceDictionary>，获取其<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>属性值，然后调用`Add`泛型`Collection`中包含的<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>。 添加的对象必须是一个新<xref:System.Windows.ResourceDictionary>。 在代码中，未设置<xref:System.Windows.ResourceDictionary.Source%2A>属性。 相反，你必须获取<xref:System.Windows.ResourceDictionary>通过创建或加载其中一个对象。 加载现有的一种方法<xref:System.Windows.ResourceDictionary>来调用<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>上的现有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]具有文件流<xref:System.Windows.ResourceDictionary>根，然后强制转换<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>返回值为<xref:System.Windows.ResourceDictionary>。  
  
### <a name="merged-resource-dictionary-uris"></a>合并资源字典 URI  
 可通过几种技术来包括合并资源字典，具体由将使用的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 格式指示。 这些技术可概括地分为两类：作为项目的一部分编译的资源，和不作为项目的一部分编译的资源。  
  
 对于作为项目的一部分编译的资源，可使用引用资源位置的相对路径。 相对路径会在编辑期间计算。 必须将资源作为“资源”生成操作定义为项目的一部分。 如果将资源 .xaml 文件作为“资源”包括在项目中，则无需将资源文件复制到输出目录，因为资源已包括在编译的应用程序中。 也可以使用“内容”生成操作，但必须将文件复制到输出目录，还需将相同路径关系中的资源文件部署到可执行文件。  
  
> [!NOTE]
>  不要使用“嵌入资源”生成操作。 支持生成操作本身[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序，但的分辨率<xref:System.Windows.ResourceDictionary.Source%2A>不会合并<xref:System.Resources.ResourceManager>，并因此不能将单个资源分离流外。 您仍可以使用嵌入的资源，出于其他目的，只要还使用<xref:System.Resources.ResourceManager>才能访问资源。  
  
 还有一种相关技术是使用指向 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件的 Pack URI，并将其作为“源”进行引用。 Pack URI 可启用对引用程序集的组件和其他技术的引用。 有关 Pack URI 的详细信息，请参阅 [WPF 应用程序资源、内容和数据文件](../app-development/wpf-application-resource-content-and-data-files.md)。  
  
 对于不作为项目的一部分编译的资源，URI 将在运行时计算。 可使用常见的 URI 传输（如 file: 或 http:）引用资源文件。 使用非编译资源方法的缺点是：file: 访问需要额外部署步骤，并且 http: 访问意味着需访问 Internet 安全区域。  
  
### <a name="reusing-merged-dictionaries"></a>重用合并字典  
 可以重复使用或在应用程序之间共享合并资源字典，因为可以通过任何有效的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 引用要合并的资源字典。 执行此操作的确切方式取决于应用程序部署策略和所遵循的应用程序模型。 前面提及的 Pack URI 策略提供了一种方法，通常可通过共享程序集引用在开发期间跨多个项目将合并资源作为源使用。 在此方案中，资源仍由客户端分发，并且至少有一个应用程序必须部署引用的程序集。 还有可能通过使用 http 协议的分布式 URI 引用合并资源。  
  
 另一种合并字典/应用程序部署的可能方案是将合并字典编写为本地应用程序文件或编写到共享存储。  
  
### <a name="localization"></a>本地化  
 如果需要本地化的资源保留为松散的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，并且隔离于将合并为主要字典的字典，则可单独本地化这些文件。 这是本地化附属资源程序集的轻量级替代方法。 有关详细信息，请参阅 [WPF 全球化和本地化概述](wpf-globalization-and-localization-overview.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.ResourceDictionary>
- [XAML 资源](xaml-resources.md)
- [资源和代码](resources-and-code.md)
- [WPF 应用程序资源、内容和数据文件](../app-development/wpf-application-resource-content-and-data-files.md)
