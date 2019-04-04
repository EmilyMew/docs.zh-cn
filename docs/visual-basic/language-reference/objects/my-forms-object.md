---
title: My.Forms 对象 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4998097b910a504461a34af3cc159ddb1c74cc62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832549"
---
# <a name="myforms-object"></a>My.Forms 对象
提供用于访问当前项目中声明每个 Windows 窗体的实例的属性。  
  
## <a name="remarks"></a>备注  
 `My.Forms`对象提供当前项目中每个窗体的实例。 该属性所访问的窗体的名称相同的属性的名称。   
  
 您可以访问提供的窗体`My.Forms`对象使用的窗体，而无需限定名称。 由于属性名称是窗体的类型名称相同，这样即可访问窗体，如同它具有默认实例。 例如，`My.Forms.Form1.Show` 与 `Form1.Show` 等效。  
  
 `My.Forms`对象公开仅与当前项目关联的窗体。 它不提供对窗体在被引用的 Dll 中声明的访问。 若要访问 DLL 提供的窗体，必须使用窗体，作为写入的限定的名称*DllName*。*窗体名称*。  
  
 可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>属性来获取应用程序的所有打开窗体的集合。  
  
 仅适用于 Windows 应用程序对象和其属性。  
  
## <a name="properties"></a>属性  
 每个属性`My.Forms`对象提供对当前项目中的窗体的实例访问。 属性的名称的窗体的属性访问，名称相同，属性类型是窗体的类型相同。  
  
> [!NOTE]
>  如果没有名称冲突，是要访问窗体的属性名称*RootNamespace*_*Namespace*\_*窗体名称*。 例如，考虑名为两个窗体`Form1.`这些窗体的其中一个是否在根命名空间`WindowsApplication1`和命名空间`Namespace1`，将访问通过该窗体`My.Forms.WindowsApplication1_Namespace1_Form1`。  
  
 `My.Forms`对象提供对在启动时创建的应用程序的主窗体的实例访问。 对于所有其他窗体，`My.Forms`对象时它将访问并将其存储创建窗体的新实例。 后续尝试访问该属性返回该窗体的实例。  
  
 您可以通过将分配释放窗体的`Nothing`到该窗体的属性。 属性 setter 调用<xref:System.Windows.Forms.Form.Close%2A>方法的窗体，然后分配`Nothing`与存储的值。 如果不是将任何值赋`Nothing`与属性 setter 引发<xref:System.ArgumentException>异常。  
  
 你可以测试的属性是否`My.Forms`对象将窗体的实例存储通过使用`Is`或`IsNot`运算符。 可以使用这些运算符来检查属性的值是否为`Nothing`。  
  
> [!NOTE]
>  通常情况下，`Is`或`IsNot`操作员必须读取的属性进行比较的值。 但是，如果该属性将当前存储`Nothing`，该属性创建窗体的新实例，然后返回该实例。 但是，Visual Basic 编译器处理的属性`My.Forms`对象以不同的方式，并允许`Is`或`IsNot`运算符来检查属性的状态，而无需更改其值。  
  
## <a name="example"></a>示例  
 此示例将更改的默认标题`SidebarMenu`窗体。  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 对于此示例正常工作，你的项目必须具有名为窗体`SidebarMenu`。  
  
 此代码将仅适用于 Windows 应用程序项目。  
  
## <a name="requirements"></a>要求  
  
### <a name="availability-by-project-type"></a>项目类型的可用性  
  
|项目类型|可用|  
|---|---|  
|Windows 应用程序|**是**|  
|类库|否|  
|控制台应用程序|否|  
|Windows 控件库|否|  
|Web 控件库|否|  
|Windows 服务|否|  
|网站|否|  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [对象](../../../visual-basic/language-reference/objects/index.md)
- [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [访问应用程序窗体](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
