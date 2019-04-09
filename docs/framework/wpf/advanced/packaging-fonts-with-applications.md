---
title: 将字体与应用程序一起打包
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: fb91d4b413db512021b90f0d4ba3049fe7333601
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123783"
---
# <a name="packaging-fonts-with-applications"></a>将字体与应用程序一起打包
本主题提供概述了如何使用包字体在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]应用程序。  
  
> [!NOTE]
>  与大多数软件类型一样，字体文件也采用许可模式，而不是出售。 许可证来控制字体使用不同供应商，但一般情况下大多数许可证，包括那些涵盖字体[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]提供与应用程序和[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，不允许将字体嵌入应用程序中或以其他方式重新分发。 因此，开发人员有责任确保自己具备必要的许可权，可以在应用程序中嵌入相应的字体或者以其他方式重新分布。  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>字体打包简介  
 您可以轻松地字体作为资源打包在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序显示用户界面文本和其他类型的文本基于内容。 字体可以与应用程序的程序集文件分开，也可以嵌入到这些程序集文件中。 还可以创建纯资源字体库，以供应用程序引用。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 和[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字体包含类型标志 fsType，指示字体的字体嵌入许可权。 但是，这个类型标志仅引用存储在文档中的嵌入字体，而不引用嵌入到应用程序中的字体。 您可以检索字体的字体嵌入字体的权限通过创建<xref:System.Windows.Media.GlyphTypeface>对象并引用其<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>属性。 请参阅的"OS/2 和 Windows 指标"部分[OpenType 规范](https://www.microsoft.com/typography/otspec/os2.htm)有关 fsType 标志的详细信息。  
  
 [Microsoft 版式](https://docs.microsoft.com/typography/)网站包括可帮助您找到特定的字体供应商或查找自定义工作的字体供应商的联系信息。  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>将字体作为内容项添加  
 可以将字体作为项目内容项添加到应用程序中，这些项目内容项与应用程序的程序集文件是分开的。 这意味着内容项不会作为程序集中的资源嵌入。 以下项目文件示例演示如何定义内容项。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 为了确保应用程序可以在运行时使用字体，这些字体必须能够从应用程序的部署目录中访问。 `<CopyToOutputDirectory>`应用程序的项目文件中的元素可用于将字体自动复制到应用程序部署目录在生成过程。 以下项目文件示例演示如何将字体复制到部署目录中。  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 以下代码示例演示如何将应用程序的字体作为内容项来引用，所引用的内容项必须与应用程序的程序集文件位于同一个目录中。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>将字体作为资源项添加  
 可以将字体作为项目资源项添加到应用程序中，这些项目资源项会嵌入到应用程序的程序集文件中。 对资源使用单独的子目录有助于对应用程序的项目文件进行整理。 以下项目文件示例演示如何在单独的子目录中将字体定义为资源项。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  时将字体作为资源添加到你的应用程序时，请确保您设置`<Resource>`元素，而不`<EmbeddedResource>`应用程序的项目文件中的元素。 `<EmbeddedResource>`不支持生成操作的元素。  
  
 以下标记示例演示如何引用应用程序的字体资源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>在代码中引用字体资源项  
 若要从代码中引用字体资源项，必须提供两个部分组成的字体资源引用： 基[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; 和字体位置引用。 这些值用作参数<xref:System.Windows.Media.FontFamily.%23ctor%2A>方法。 下面的代码示例演示如何引用名为的项目子目录中的应用程序的字体资源`resources`。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]可以包括字体资源所在的应用程序子目录。 在这种情况下，字体位置引用不需要指定一个目录，但必须包括前缀"`./`"，指示字体资源是指定的基的相同目录中[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。 以下代码示例演示另一种引用字体资源项的方法，该示例与上面的代码示例等效。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>在同一应用程序子目录中引用字体  
 可以将应用程序内容和资源文件放在应用程序项目中由用户定义的同一子目录中。 以下项目文件示例显示在同一子目录中定义的内容页和字体资源。  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 由于应用程序内容和字体位于同一子目录中，因此字体引用是相对于应用程序内容的。 以下示例演示当字体与应用程序位于同一目录中时，如何引用应用程序的字体资源。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>在应用程序中枚举字体  
 若要枚举字体作为资源应用程序中的项，请使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>或<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法。 下面的示例演示如何使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>方法返回的集合<xref:System.Windows.Media.FontFamily>从应用程序字体位置的对象。 在本示例中，应用程序包含一个名为“resources”的子目录。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 下面的示例演示如何使用<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法返回的集合<xref:System.Windows.Media.Typeface>从应用程序字体位置的对象。 在本示例中，应用程序包含一个名为“resources”的子目录。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>创建字体资源库  
 可以创建仅包含字体的纯资源库，这种类型的库项目中没有任何代码。 创建纯资源库是将资源与使用它们的应用程序代码分开的一种常用方法。 这还使得库程序集可以包括在多个应用程序项目中。 以下项目文件示例演示纯资源库项目的关键部分。  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a>引用资源库中的字体  
 若要在应用程序中引用资源库中的字体，必须将库程序集的名称作为字体引用的前缀。 在本例中，字体资源程序集是“FontLibrary”。 若要将程序集名称与程序集内的引用分开，请使用“;”字符。 添加后跟字体名引用的“Component”关键字即完成字体库资源的完整引用。 以下代码示例演示如何引用资源库程序集内的字体。  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  此 SDK 包含一组示例[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]您可以使用的字体[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序。 这些字体是在纯资源库中定义的。 有关详细信息，请参阅[示例 OpenType 字体包](sample-opentype-font-pack.md)。  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>字体的使用限制  
 以下列表介绍上打包和字体中使用的几个限制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序：  
  
-   **字体嵌入权限位：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不检查或实施任何字体嵌入权限位。 请参阅[Introduction_to_Packing Fonts](#introduction_to_packaging_fonts)部分，了解详细信息。  
  
-   **源字体站点：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许对 http 或 ftp 的字体引用[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。  
  
-   **使用包的绝对 URI： 表示法：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序不允许您创建<xref:System.Windows.Media.FontFamily>对象以编程方式使用"pack:"作为一部分绝对[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]对字体引用。 例如，`"pack://application:,,,/resources/#Pericles Light"`是无效的字体引用。  
  
-   **自动嵌入字体：** 在设计时，没有用于搜索应用程序使用的字体和自动在应用程序的资源中嵌入字体支持。  
  
-   **字体子集：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序不支持为非固定文档创建字体子集。  
  
-   如果存在不正确的引用，应用程序将回退到使用可用字体。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft 版式：链接、 新闻和联系人](https://docs.microsoft.com/typography/)
- [OpenType 规范](https://www.microsoft.com/typography/otspec/)
- [OpenType 字体功能](opentype-font-features.md)
- [示例 OpenType 字体包](sample-opentype-font-pack.md)
