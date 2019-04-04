---
title: 示例业务方案和无服务器应用的用例
description: 通过访问范围的示例从映像处理到移动后端和 ETL 管道了解亲自动手实践的无服务器体验。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 177fb1d7f79a0067ab185e520778b593d4b8eaf6
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653894"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>无服务器业务方案和用例

有许多用例和方案的无服务器应用程序。 本章包括示例，用于演示不同的方案。 方案包括指向相关的文档和公共源代码存储库。 这一章中的示例，可以开始您自己构建和实现无服务器解决方案。

## <a name="analyze-and-archive-images"></a>分析和归档图像

此示例演示无服务器事件 （事件网格）、 工作流 （逻辑应用） 和代码 (Azure Functions)。 它还演示如何将与另一个资源，图像分析此事例认知服务中进行集成。

控制台应用程序，可传递一个链接到的 URL 在 web 上找到。 应用程序发布 URL 作为事件网格消息。 并行情况下，无服务器函数应用和逻辑应用订阅该消息。 无服务器函数应用序列化到 blob 存储的映像。 它还存储在 Azure 表存储中的信息。 元数据将存储原始图像 URL 和 blob 映像的名称。 逻辑应用使用自定义视觉 API 分析图像并创建计算机生成的标题进行交互。 标题存储在元数据表中。

![分析和归档映像体系结构](./media/image-processing-example.png)

单独的单页应用程序 (SPA) 调用来获取的图像和元数据列表的无服务器函数。 对于每个映像，它将调用从存档中提供的图像数据的另一个函数。 最终结果是具有自动字幕的库。

![自动化的图像库](./media/automated-image-gallery.png)

完整的存储库并说明如何构建逻辑应用位于以下位置：[事件网格粘附](https://github.com/JeremyLikness/Event-Grid-Glue)。

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>跨平台移动客户端使用 Xamarin.Forms 和函数

了解如何在 Azure Web 门户中或在 Visual Studio 中实现一个简单的无服务器 Azure 函数。 生成 Android、 iOS 和 Windows 运行的 Xamarin.Forms 具有的客户端。 应用程序然后优化为服务器和使用无服务器的后端的移动客户端之间的通信中使用 JavaScript 对象表示法 (JSON)。

有关详细信息，请参阅[使用 Xamarin.Forms 客户端和实施一个简单的 Azure 函数](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>生成无服务器的图像识别与照片马赛克

该示例使用 Azure Functions 和 Microsoft 认知服务自定义影像服务从输入图像生成照片马赛克。 训练模型来识别图像。 上传图像时，它可以识别图像，并使用必应搜索。 原始图像是重新组合使用搜索结果。

![奥兰多关注照片和马赛克](./media/orlando-eye-both.png)

例如，你可以训练奥兰多的地标，例如奥兰多关注与您的模型。 自定义影像将识别的奥兰多只眼，映像并为该函数将创建照片马赛克组成必应图像搜索结果"奥兰多眼。"

有关详细信息，请参阅[Azure Functions 照片马赛克生成器](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)。

## <a name="migrate-an-existing-application-to-the-cloud"></a>迁移到云的现有应用程序

如前面几章中所述，很常见欣然接受要在应用程序在本地托管的 N 层体系结构。 尽管迁移资源"按原样"使用虚拟机到云至少风险的路径，许多公司选择使用机会来重构其应用程序。 幸运的是，重构不一定要"要么"的工作。 事实上，它是可以迁移您的应用程序然后段落组件将替换为云本机函数。

应用程序使用 Azure Functions 代理功能使重构到无服务器终结点的终结点从旧的本地代码。

![迁移体系结构](./media/migration-architecture.png)

代理提供了更新以将单个请求重新路由，因为它们将被移动到无服务器函数的单个 API 终结点。

您可以查看视频，介绍了如何通过在整个迁移：[提升和转移无服务器 Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102)。 访问示例代码：[将你自己的应用](https://github.com/JeremyLikness/bring-own-app-connect-17)。

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>分析 CSV 文件并将插入到数据库

提取、 转换和加载 (ETL) 是集成不同的系统的常见业务函数。 设置专用的 FTP 服务器，然后部署计划的作业来分析文件并将它们转换用于商业用途，通常涉及到传统的方法。 无服务器体系结构使作业更容易，因为该文件上传时为可以激发触发器。 Azure 函数处理任务，如通过专注于特定的问题小代码段其理想组合 ETL。

![显示 csv 分析过程的屏幕截图。](./media/serverless-business-scenarios/csv-parse-database-import.png)

源代码和动手实验，请参阅[CSV 导入实验室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。

## <a name="shorten-links-and-track-metrics"></a>请缩短链接，然后跟踪指标

最初帮助简单地说编码 Url 的链接缩短工具 twitter 帖子，以适应 140 个字符限制。 它们已发展起来，包含几种用法，通常以跟踪各单击操作进行分析。 链接 shortener 示例方案是完全无服务器应用程序的管理链接和报告指标。

Azure 函数用于为单页应用程序 (SPA)，您可以将长 URL 粘贴并生成短 Url 提供服务。 Url 标记来跟踪活动 （主题） 和媒体 （如链接发布到的社交网络） 等内容。 短代码作为键，作为值的长 url 存储在 Azure 表存储中。 单击的短链接时，另一个函数查找长 URL、 发送重定向，并将有关事件的信息放在队列上。 另一个 Azure 函数处理队列，并将放入 Azure Cosmos DB 的信息。

![链接 shortener 示例体系结构](./media/link-shortener-architecture.png)

然后，可以创建 Power BI 仪表板来收集有关收集的数据的见解。 在后端，Application Insights 提供了重要的指标。 遥测数据包括需要多长时间的平均用户重定向和访问 Azure 表存储所需的时间长度。

![Power BI 示例](./media/power-bi-example.png)

此处提供了说明的完整链接 shortener 示例存储库：[无服务器的 URL shortener 示例](https://github.com/jeremylikness/serverless-url-shortener)。 你可以阅读此处的简化版本：[以分钟为单位的无服务器.NET 应用程序的 azure 存储](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)。

## <a name="verify-device-connectivity-using-a-ping"></a>验证使用 ping 的设备连接

此示例包含的 Azure IoT 中心和 Azure 函数。 IoT 中心中的新消息触发 Azure 函数。 无服务器代码返回到发送它的设备发送同一消息内容。 项目都有解决方案所需的所有代码和部署配置。

有关详细信息，请参阅[Azure IoT 中心 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)。

## <a name="recommended-resources"></a>推荐的资源

* [Azure Functions 照片马赛克生成器](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT 中心 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [以分钟为单位的无服务器.NET 应用程序的 azure 存储](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [将你自己的应用](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV 导入实验室](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [事件网格粘附](https://github.com/JeremyLikness/Event-Grid-Glue)
* [使用 Xamarin.Forms 客户端和实施一个简单的 Azure 函数](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [提升和转移无服务器 Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102)
* [无服务器的 URL shortener 示例](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[上一页](orchestration-patterns.md)
>[下一页](serverless-conclusion.md)