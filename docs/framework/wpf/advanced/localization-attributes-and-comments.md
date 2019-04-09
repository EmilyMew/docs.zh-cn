---
title: 本地化特性和注释
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4e4c4891a905a5e4458ad5fc21a512c1dfe6f74e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092911"
---
# <a name="localization-attributes-and-comments"></a>本地化特性和注释
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 本地化注释内部是属性，[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]源代码，提供的开发人员能够提供本地化规则和提示。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 本地化注释包含两个集的信息： 可本地化性特性和任意形式的本地化注释。 可本地化特性由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 本地化 API 用于指示哪些资源要进行本地化。 任意形式的注释是应用程序作者希望包含的任何信息。  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>本地化注释  
 如果标记应用程序作者对 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 中的特定元素具有一定的要求（如对文本长度、字体系列或字号进行约束），则他们可以借助于 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 代码中的注释将此信息传达给本地化人员。 下面是用来向源代码中添加注释的过程：  
  
1.  应用程序开发人员向 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 源代码中添加本地化注释。  
  
2.  在生成过程中，可以在 .proj 文件中指定是将任意形式的本地化注释留在程序集内、去掉部分注释还是去掉所有注释。 去掉的注释放在一个单独的文件中。 可以使用 `LocalizationDirectivesToLocFile` 标记指定你的选项，例如：  
  
     `<LocalizationDirectivesToLocFile>` *值* `</LocalizationDirectivesToLocFile>`  
  
3.  可以分配的值包括：  
  
    -   **None** - 注释和特性都保留在程序集中，不会生成单独的文件。  
  
    -   **CommentsOnly** - 仅从程序集中去掉注释，并将它们放在单独的 LocFile 中。  
  
    -   **All** - 从程序集中去掉注释和特性，并将它们两者都放在单独的 LocFile 中。  
  
4.  从 [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 中提取可本地化资源时，可本地化性特性将由 [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 本地化 API 保留。  
  
5.  以后可以将仅包含任意形式的注释的本地化注释文件合并到本地化过程中。  
  
 以下示例演示如何将本地化注释添加到 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 文件中。  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 在上一示例中，Localization.Attributes 部分包含本地化特性，Localization.Comments 部分包含任意形式的注释。 下表显示了特性和注释及其对于本地化人员的含义。  
  
|本地化特性|含义|  
|-----------------------------|-------------|  
|$Content（不可修改的可读文本）|无法修改 TextBlock 元素的内容。 本地化人员不能更改单词“Microsoft”。 内容对本地化人员可见（可读）。 内容为文本类别。|  
|FontFamily（不可修改但可读）|无法更改 TextBlock 元素的字体系列属性，但该属性对本地化人员可见。|  
  
|本地化任意形式的注释|含义|  
|--------------------------------------|-------------|  
|$Content（商标）|应用程序作者告知本地化人员 TextBlock 元素中的内容是商标。|  
|FontSize（商标字号）|应用程序作者指示字号属性应遵循标准商标大小。|  
  
### <a name="localizability-attributes"></a>可本地化特性  
 Localization.Attributes 中的信息包含对的列表：目标值名称和关联的可本地化值。 目标名称可以是属性名称或特殊 $Content 名称。 如果是属性名称，则目标值为属性的值。 如果是 $Content，则目标值为元素的内容。  
  
 有三种类型的特性：  
  
-   **Category**。 它指定是否可以从本地化工具修改值。 请参阅 <xref:System.Windows.LocalizabilityAttribute.Category%2A>。  
  
-   **Readability**。 它指定本地化工具是否可读取（和显示）值。 请参阅 <xref:System.Windows.LocalizabilityAttribute.Readability%2A>。  
  
-   **Modifiability**。 它指定本地化工具是否允许修改值。 请参阅 <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>。  
  
 这些特性可以按照由空格分开的任何顺序进行指定。 如果指定了重复特性，则最后一个特性将替代前面的特性。 例如，Localization.Attributes = "Unmodifiable Modifiable" 会将 Modifiability 设置为 Modifiable，因为最后一个值是 Modifiable。  
  
 Modifiability 和 Readability 的名称已经揭示了自身的含义。 “Category”特性提供的预定义类别可帮助本地化人员翻译文本。 类别（如 Text、Label 和 Title）为本地化人员提供了有关如何翻译文本的信息。 也有一些特殊类别：无、 继承、 忽略，和 NeverLocalize。  
  
 下表显示了这些特殊类别的含义。  
  
|类别|含义|  
|--------------|-------------|  
|None|没有为目标值定义类别。|  
|继承|目标值从其父级继承其类别。|  
|忽略|在本地化过程中将忽略目标值。 Ignore 仅影响当前值。 它不会影响子节点。|  
|NeverLocalize|无法对当前值进行本地化。 此类别由元素的子级继承。|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>本地化注释  
 Localization.Comments 包含与目标值有关的任意形式的字符串。 应用程序开发人员可以添加一些信息，以便为本地化人员提供有关如何翻译应用程序文本的提示。 注释格式可以是由“()”括起来的任何字符串。 可以使用“\\”对字符进行转义。  
  
## <a name="see-also"></a>请参阅

- [WPF 的全球化](globalization-for-wpf.md)
- [使用自动布局创建按钮](how-to-use-automatic-layout-to-create-a-button.md)
- [使用网格进行自动布局](how-to-use-a-grid-for-automatic-layout.md)
- [对应用程序进行本地化](how-to-localize-an-application.md)
