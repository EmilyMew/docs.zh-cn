---
title: My.WebServices 对象 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a60f32c4f581e42f240fca55ce496776c5511ba3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840427"
---
# <a name="mywebservices-object"></a>My.WebServices 对象
提供用于创建和访问当前项目所引用的每个 XML Web 服务的单个实例的属性。  
  
## <a name="remarks"></a>备注  
 `My.WebServices` 对象提供当前项目所引用的每个 Web 服务的实例。 按需实例化每个实例。 可以通过 `My.WebServices` 对象的属性访问这些 Web 服务。 该属性的名称与该属性所访问的 Web 服务的名称相同。 任何自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 继承的类均为 Web 服务。 有关将 Web 服务添加到项目的信息，请参阅[访问应用程序 Web 服务](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 `My.WebServices`对象公开的与当前项目相关联的 Web 服务。 它不提供对被引用的 Dll 中声明的 Web 服务的访问。 若要访问 DLL 提供的 Web 服务，必须使用 Web 服务的限定的名形式*DllName*。*WebServiceName*。 有关详细信息，请参阅[访问应用程序 Web 服务](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 对象和其属性不适用于 Web 应用程序。  
  
## <a name="properties"></a>属性  
 每个属性`My.WebServices`对象提供对当前项目所引用的 Web 服务的实例访问。 属性的名称访问该属性，Web 服务的名称相同，属性类型是 Web 服务的类型相同。  
  
> [!NOTE]
>  如果没有名称冲突，用于访问 Web 服务的属性名称是*RootNamespace*_*Namespace*\_*ServiceName*。 例如，考虑名为两个 Web 服务`Service1`。 如果这些服务之一就是根命名空间`WindowsApplication1`和命名空间中`Namespace1`，将使用访问该服务`My.WebServices.WindowsApplication1_Namespace1_Service1`。  
  
 当首次访问之一`My.WebServices`对象的属性，它将创建 Web 服务的新实例并将其存储。 该属性的后续访问返回的 Web 服务的实例。  
  
 您可以通过将分配释放 Web 服务的`Nothing`到该 Web 服务的属性。 属性 setter 将分配`Nothing`与存储的值。 如果不是将任何值赋`Nothing`与属性 setter 引发<xref:System.ArgumentException>异常。  
  
 你可以测试的属性是否`My.WebServices`对象将 Web 服务的实例存储通过使用`Is`或`IsNot`运算符。 可以使用这些运算符来检查属性的值是否为`Nothing`。  
  
> [!NOTE]
>  通常情况下，`Is`或`IsNot`操作员必须读取的属性进行比较的值。 但是，如果该属性将当前存储`Nothing`，该属性创建 Web 服务的新实例，然后返回该实例。 但是，Visual Basic 编译器处理的属性`My.WebServices`对象，并允许`Is`或`IsNot`运算符来检查属性的状态，而无需更改其值。  
  
## <a name="example"></a>示例  
 此示例调用`FahrenheitToCelsius`方法的`TemperatureConverter`XML Web 服务，并返回结果。  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 此示例正常工作，为你的项目必须引用一个名为 Web 服务`Converter`，并且该 Web 服务必须公开`ConvertTemperature`方法。 有关详细信息，请参阅[访问应用程序 Web 服务](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 此代码不适用于 Web 应用程序项目。  
  
## <a name="requirements"></a>要求  
  
### <a name="availability-by-project-type"></a>项目类型的可用性  
  
|项目类型|可用|  
|---|---|  
|Windows 应用程序|**是**|  
|类库|**是**|  
|控制台应用程序|**是**|  
|Windows 控件库|**是**|  
|Web 控件库|**是**|  
|Windows 服务|**是**|  
|网站|否|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [访问应用程序 Web 服务](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
