---
title: My.Resources 对象 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ee4d30b82ceada5c4f3fc4ad95dc8eeedd9355b0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821733"
---
# <a name="myresources-object"></a>My.Resources 对象
提供用于访问应用程序的资源的属性和类。  
  
## <a name="remarks"></a>备注  
 `My.Resources`对象提供了对应用程序的资源的访问，并允许动态应用程序的检索资源。 有关详细信息，请参阅[管理应用程序资源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources`对象公开只有全局资源。 它不提供对与窗体相关联的资源文件的访问。 必须从窗体来访问窗体资源。  
  
 您可以访问应用程序的特定于区域性的资源文件从`My.Resources`对象。 默认情况下`My.Resources`对象查找匹配的区域中的资源文件中的资源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>属性。 但是，可以重写此行为，并指定特定区域性的资源使用。 有关详细信息，请参阅[桌面应用中的资源](../../../framework/resources/index.md)。  
  
## <a name="properties"></a>属性  
 属性`My.Resources`对象提供对应用程序的资源的只读访问。 若要添加或删除资源，请使用**项目设计器**。 您可以访问资源通过添加**项目设计器**通过使用`My.Resources.` *resourceName*。  
  
 此外可以添加或删除选择的项目中的资源文件**解决方案资源管理器**，然后单击**添加新项**或**添加现有项**从**项目**菜单。 您可以访问资源使用，以这种方式添加了`My.Resources.` *resourceFileName*`.`*resourceName*。  
  
 每个资源都有名称、 类别和值，并且这些资源设置确定要访问的资源的属性中的显示方式`My.Resources`对象。 在中添加的资源**项目设计器**:  
  
-   名称确定属性的名称  
  
-   资源数据是属性的值  
  
-   类别设置确定属性的类型：  
  
|类别|属性数据类型|  
|---|---|  
|**字符串**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**图像**|<xref:System.Drawing.Bitmap>|  
|**图标**|<xref:System.Drawing.Icon>|  
|**音频**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>类派生自<xref:System.IO.Stream>类，因此它可以用于采用流，例如方法<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。|  
|**文件**|-   [字符串](../../../visual-basic/language-reference/data-types/string-data-type.md)的文本文件。<br />-   <xref:System.Drawing.Bitmap> 为图像文件。<br />-   <xref:System.Drawing.Icon> 图标文件。<br />-   <xref:System.IO.UnmanagedMemoryStream> 声音文件。|  
|**其他**|通过在设计器中的信息确定**类型**列。|  
  
## <a name="classes"></a>类  
 `My.Resources`对象将作为具有共享属性的类公开的每个资源文件。 类名是资源文件的名称相同。 如前一部分中所述，在资源文件中的资源被称为类中的属性。  
  
## <a name="example"></a>示例  
 此示例将窗体的标题设置为命名的字符串资源`Form1Title`在应用程序资源文件中。 若要运行示例，应用程序必须具有一个名为字符串`Form1Title`其资源文件中。  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>示例  
 此示例设置窗体的图标名为的图标为`Form1Icon`存储在应用程序的资源文件。 若要运行示例，应用程序必须具有名为一个图标`Form1Icon`其资源文件中。  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>示例  
 此示例将一个窗体的背景图像设置为命名的图像资源`Form1Background`，这是应用程序资源文件中。 此示例正常工作，应用程序必须有一个名为映像资源`Form1Background`其资源文件中。  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>示例  
 此示例中播放的声音，存储为一个名为的音频资源`Form1Greeting`在应用程序的资源文件中。 若要运行示例，该应用程序必须具有一个名为的音频资源`Form1Greeting`其资源文件中。 `My.Computer.Audio.Play`方法是仅适用于 Windows 窗体应用程序。  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>示例  
 此示例检索字符串资源的应用程序的法语区域性版本。 资源名为`Message`。 若要更改区域性的`My.Resources`对象使用，该示例使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。  
  
 此示例正常工作，程序必须具有一个名为字符串`Message`在其资源文件和应用程序应具有的资源文件，Resources.fr-FR.resx 法语区域性版本。 如果应用程序不具有的资源文件中，法语区域性版本`My.Resource`对象将从默认区域性资源文件中检索资源。  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>请参阅

- [管理应用程序资源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [桌面应用中的资源](../../../framework/resources/index.md)
