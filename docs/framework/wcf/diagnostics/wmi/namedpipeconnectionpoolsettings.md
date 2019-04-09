---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095329"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>语法  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>方法  
 NamedPipeConnectionPoolSettings 类不定义任何方法。  
  
## <a name="properties"></a>属性  
 NamedPipeConnectionPoolSettings 类具有以下属性：  
  
### <a name="groupname"></a>GroupName  
 数据类型：String  
  
 访问类型：只读  
  
 绑定元素使用的连接池的组名。  
  
### <a name="idletimeout"></a>IdleTimeout  
 数据类型：DateTime  
  
 访问类型：只读  
  
 连接在断开前可以空闲的最长时间。  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 数据类型：sint32  
  
 访问类型：只读  
  
 客户端上每个终结点的最大出站连接数。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
