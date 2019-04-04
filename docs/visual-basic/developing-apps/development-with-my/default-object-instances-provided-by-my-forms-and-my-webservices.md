---
title: My.Forms 和 My.WebServices 提供的默认对象实例 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839353"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms 和 My.WebServices 提供的默认对象实例 (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)并[My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)对象提供对窗体、 数据源和 XML Web 服务使用你的应用程序的访问权限。 它们执行此操作的集合，从而*默认实例*的每个对象。  
  
## <a name="default-instances"></a>默认实例  
 默认实例是由运行时提供，不需要进行的类的实例声明并实例化使用`Dim`和`New`语句。 下面的示例演示如何必须声明和实例化的实例<xref:System.Windows.Forms.Form>类调用`Form1`，，如何现在能够获得的默认实例<xref:System.Windows.Forms.Form>类通过`My.Forms`。  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`对象返回的默认实例的集合，每个`Form`在项目中存在的类。 同样，`My.WebServices`提供你的应用程序中创建了对引用的每个 Web 服务代理类的默认实例。  
  
## <a name="see-also"></a>请参阅

- [My.Forms 对象](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices 对象](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [My 对项目类型的依赖方式](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
