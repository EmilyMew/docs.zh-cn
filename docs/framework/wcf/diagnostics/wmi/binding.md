---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106510"
---
# <a name="binding"></a>绑定
wmi Binding  
  
## <a name="syntax"></a>语法  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>方法  
 Binding 类未定义任何方法。  
  
## <a name="properties"></a>属性  
 Binding 类具有以下属性。  
  
### <a name="bindingelements"></a>BindingElements  
 数据类型：BindingElement 数组  
  
 访问类型：只读  
  
 由绑定实现的绑定元素的集合。  
  
### <a name="closetimeout"></a>CloseTimeout  
 数据类型：DateTime  
  
 访问类型：只读  
  
 为完成关闭操作提供的时间间隔。  
  
### <a name="name"></a>名称  
 数据类型：String  
  
 访问类型：只读  
  
 绑定的名称。  
  
### <a name="namespace"></a>命名空间  
 数据类型：String  
  
 访问类型：只读  
  
 绑定的 XML 命名空间。  
  
### <a name="opentimeout"></a>OpenTimeout  
 数据类型：DateTime  
  
 访问类型：只读  
  
 为完成打开操作提供的时间间隔。  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 数据类型：DateTime  
  
 访问类型：只读  
  
 为完成接收操作提供的时间间隔。  
  
### <a name="scheme"></a>方案  
 数据类型：String  
  
 访问类型：只读  
  
 绑定建立的通道和侦听器工厂所使用的 URI 传输方案。  
  
### <a name="sendtimeout"></a>SendTimeout  
 数据类型：DateTime  
  
 访问类型：只读  
  
 为完成发送操作提供的时间间隔。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.Binding>
