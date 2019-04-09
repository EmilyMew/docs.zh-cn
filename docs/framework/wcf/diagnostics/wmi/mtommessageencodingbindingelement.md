---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140473"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>语法  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>方法  
 MtomMessageEncodingBindingElement 类不定义任何方法。  
  
## <a name="properties"></a>属性  
 MtomMessageEncodingBindingElement 类具有以下属性：  
  
### <a name="encoding"></a>编码  
 数据类型：String  
  
 访问类型：只读  
  
 要用来在绑定上发出消息的字符集编码。  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 数据类型：sint32  
  
 访问类型：只读  
  
 一个整数，指定在无需分配新读取器的情况下可以同时读取的消息数。  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 数据类型：sint32  
  
 访问类型：只读  
  
 一个整数，指定在无需分配新编写器的情况下可以同时发送的消息数。  
  
### <a name="readerquotas"></a>ReaderQuotas  
 数据类型：XmlDictionaryReaderQuotas  
  
 访问类型：只读  
  
 读取器的配额。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
