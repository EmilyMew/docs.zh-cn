---
title: 未指定启动窗体
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 9af95b397bef4a19654510619cf0864c8ab7b76f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833563"
---
# <a name="a-startup-form-has-not-been-specified"></a>未指定启动窗体
应用程序使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>类，但未指定启动窗体。  
  
 发生这种情况**启用应用程序框架**项目设计器中选中复选框，但**启动窗体**未指定。 有关详细信息，请参阅 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)（应用程序页、项目设计器 (Visual Basic)。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  指定应用程序的启动对象。  
  
     有关详细信息，请参阅 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)（应用程序页、项目设计器 (Visual Basic)。  
  
2.  重写<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>方法以设置<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>属性设置为启动窗体。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visual Basic 应用程序模型概述](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
