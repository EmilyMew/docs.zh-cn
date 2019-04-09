---
title: 对象具体化（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: c63dd07686463c652c27dea8473b4d8cbe2dab71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137665"
---
# <a name="object-materialization-wcf-data-services"></a>对象具体化（WCF 数据服务）
当你使用**添加服务引用**对话框，可以使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]馈送基于.NET Framework 的客户端应用程序中，等效的数据类生成的源公开的数据模型中每个实体类型。 有关详细信息，请参阅[生成数据服务客户端库](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。 查询返回的实体数据将具体化为所生成的客户端数据服务类之一的实例。 合并选项和标识解析的被跟踪的对象有关的信息，请参阅[管理数据服务上下文](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 此外可以定义自己的客户端数据服务类而不是使用工具生成数据类。 这样您便可以使用自己的数据类，也称为“纯旧式 CLR 对象”(POCO) 数据类。 使用这些类型的自定义数据类时，应属性数据类具有<xref:System.Data.Services.Common.DataServiceKeyAttribute>或<xref:System.Data.Services.Common.DataServiceEntityAttribute>，并确保上的数据服务数据模型中的客户端匹配类型名称的类型名称。  
  
 在库收到查询响应消息后，它将从返回的数据具体化[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]馈送到客户端数据的实例的查询的类型的服务类。 以下是具体化这些对象的一般过程：  
  
1.  客户端库从响应消息源中的 `entry` 元素读取序列化的类型，并尝试采用以下方法之一创建正确类型的新实例：  
  
    -   当在源中声明的类型与 <xref:System.Data.Services.Client.DataServiceQuery%601> 的类型具有相同的名称时，会使用空的构造函数创建此类型的新实例。  
  
    -   当在源中声明的类型与从 <xref:System.Data.Services.Client.DataServiceQuery%601> 的类型派生的类型具有相同的名称时，会使用空的构造函数创建此派生类型的新实例。  
  
    -   当在源中声明的类型无法与 <xref:System.Data.Services.Client.DataServiceQuery%601> 的类型或任何派生的类型相匹配时，会使用空的构造函数创建所查询类型的新实例。  
  
    -   设置 <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> 属性时，会调用提供的委托来重写基于默认名称的类型映射，并改为创建由 <xref:System.Func%602> 返回的类型的新实例。 如果此委托返回一个 null 值，则改为创建所查询类型的新实例。 可能需要重写基于默认名称的类型名称映射以支持继承方案。  
  
2.  客户端库从 `id` 的 `entry` 元素中读取 URI 值，它是实体的标识值。 除非使用 <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> 的 <xref:System.Data.Services.Client.MergeOption.NoTracking> 值，否则将使用标识值来跟踪 <xref:System.Data.Services.Client.DataServiceContext> 中的对象。 该标识值还用于保证仅创建一个实体实例，即使某个实体在查询响应中返回多次。  
  
3.  客户端库从源项中读取属性并对新创建的对象设置相应的属性。 如果具有相同标识值的对象已出现在 <xref:System.Data.Services.Client.DataServiceContext> 中，则根据 <xref:System.Data.Services.Client.MergeOption> 的 <xref:System.Data.Services.Client.DataServiceContext> 设置来设定这些属性。 响应可能包含其相应属性不出现在客户端类型中的属性值。 发生这种情况时，将根据 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 的 <xref:System.Data.Services.Client.DataServiceContext> 属性的值采取操作。 当此属性设置为 `true` 时，忽略缺少的属性。 否则将引发错误。 按如下方式设置这些属性：  
  
    -   将标量属性设置为响应消息中该项的相应值。  
  
    -   将复杂属性设置为新的复杂类型实例，其中使用响应中的复杂类型的属性设置这些属性。  
  
    -   将返回相关实体集合的导航属性设置为 <xref:System.Collections.Generic.ICollection%601> 的新实例或现有实例，其中 `T` 是相关实体的类型。 除非相关对象已加载到 <xref:System.Data.Services.Client.DataServiceContext> 中，否则此集合是空的。 有关详细信息，请参阅[加载延迟的内容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
        > [!NOTE]
        >  当生成的客户端数据类支持数据绑定时，导航属性改为返回 <xref:System.Data.Services.Client.DataServiceCollection%601> 类的实例。 有关详细信息，请参阅[数据绑定到控件](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
4.  引发 <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> 事件。  
  
5.  客户端库将该对象附加到 <xref:System.Data.Services.Client.DataServiceContext>。 当 <xref:System.Data.Services.Client.MergeOption> 为 <xref:System.Data.Services.Client.MergeOption.NoTracking> 时不附加该对象。  
  
## <a name="see-also"></a>请参阅

- [查询数据服务](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [查询投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
