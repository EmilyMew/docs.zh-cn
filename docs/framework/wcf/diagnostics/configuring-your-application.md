---
title: 配置应用程序
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 94bf5f4bbee8bb8bb462c4bf91be75d1627ec567
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087165"
---
# <a name="configuring-your-application"></a>配置应用程序
Windows Communication Foundation (WCF) 使用.NET 配置系统，并且允许您在计算机和应用程序范围配置服务。  
  
 定义的 WCF 配置设置位于`<system.serviceModel>`节组。 有关如何配置 WCF 服务的详细信息，请参阅以下主题：  
  
-   [正在配置服务](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 应用程序定义的配置设置是在 `<appSettings>` 节组中定义的。 有关.NET 配置文件中的应用程序设置的详细信息，请参阅[ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159)。  
  
## <a name="using-the-configuration-editor"></a>使用配置编辑器  
 WCF[配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)使管理员和开发人员能够创建和修改 WCF 服务使用的图形用户界面的配置设置。 利用此工具，可以管理 WCF 绑定、 行为、 服务和诊断的设置，而无需直接编辑 XML 配置文件。  
  
## <a name="editing-configuration-files-in-visual-studio"></a>在 Visual Studio 中编辑配置文件  
 若要编辑的 Visual Studio 中的 WCF 服务项目的配置文件，右键单击它以**解决方案资源管理器**，然后选择**编辑 WCF 配置**上下文菜单项。 这将启动[配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。  
  
> [!NOTE]
>  如果右键单击该中编辑配置文件的 Visual Studio 中的 WCF Web 服务项目**解决方案资源管理器**，注意**编辑 WCF 配置**上下文菜单项缺少。 解决此问题，请单击**工具**菜单，然后选择**WCF 服务配置编辑器**。 之后，可以右键单击配置文件，并使用**编辑 WCF 配置**上下文菜单项。  
  
## <a name="see-also"></a>请参阅

- [配置编辑器工具 (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [正在配置服务](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
