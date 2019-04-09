---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179148"
---
# <a name="transactionflow"></a>\<transactionFlow>
指定自定义绑定的事务流支持。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<transactionFlow>  
  
## <a name="syntax"></a>语法  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|transactionProtocol|指定要使用的事务处理协议。 包括以下有效值：<br /><br /> -   OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> 默认值为 OleTransactions。<br /><br /> 此属性的类型为 <xref:System.ServiceModel.TransactionProtocol>。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定义自定义绑定的所有绑定功能。|  
  
## <a name="remarks"></a>备注  
 此元素允许你在终结点绑定设置中启用或禁用传入事务流，并允许指定传入事务所需的协议格式。 使用此配置元素的详细信息，请参阅[ServiceModel 事务配置](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)并[启用事务流](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。  
  
> [!CAUTION]
>  使用 `OleTransactions` 协议在终结点之间对事务进行流处理时，如果目标终结点尝试使用任何 `OleTransactions` 之外的协议进行流处理，则可能丢失事务超时。 这可能导致 OleTransactions 跃点后面的所有下级节点的超时时间比预期延迟。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [ServiceModel 事务配置](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [启用事务流](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [扩展绑定](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
