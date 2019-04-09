---
title: 如何：实现异步服务操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 8d11f39942793414e9e800b4e180d4d5ed5b2a3a
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055152"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>如何：实现异步服务操作
在 Windows Communication Foundation (WCF) 应用程序中的服务操作可以实现异步还是同步而无需指示客户端如何调用它。 例如，可以同步，调用异步服务操作和同步服务操作可以异步调用。 有关演示如何在客户端应用程序中以异步方式调用操作的示例，请参阅[如何：以异步方式调用服务操作](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。 有关同步和异步操作的详细信息，请参阅[Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)并[同步和异步操作](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。 本主题介绍异步服务操作的基本结构，代码并不完整。 服务和客户端的完整示例，请参阅[异步](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100))。  
  
### <a name="implement-a-service-operation-asynchronously"></a>按异步方式实现服务操作  
  
1.  在服务协定中，按照 .NET 异步设计准则声明一个异步方法对。 `Begin` 方法采用一个参数、一个回调对象和一个状态对象作为参数，并且返回一个 <xref:System.IAsyncResult?displayProperty=nameWithType> 和一个匹配的 `End` 方法，该方法采用一个 <xref:System.IAsyncResult?displayProperty=nameWithType> 作为参数并将返回值返回。 有关异步调用的详细信息，请参阅[异步编程设计模式](https://go.microsoft.com/fwlink/?LinkId=248221)。  
  
2.  使用 `Begin` 属性 (attribute) 标记该异步方法对的 <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 方法，并将 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> 属性 (property) 设置为 `true`。 例如，下面的代码执行步骤 1 和 2。  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  按照异步设计准则在服务类中实现 `Begin/End` 方法对。 例如，下面的代码示例演示一个实现，在此实现中，异步服务操作的 `Begin` 和 `End` 部分都向控制台写入一个字符串，并且将 `End` 操作的返回值返回到客户端。 有关完整的代码示例，请参见“示例”部分。  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>示例  
 下面的代码示例演示以下各项：  
  
1.  与下列各项之间的服务协定接口：  
  
    1.  同步 `SampleMethod` 操作。  
  
    2.  异步 `BeginSampleMethod` 操作。  
  
    3.  异步`BeginServiceAsyncMethod` / `EndServiceAsyncMethod`操作对。  
  
2.  使用 <xref:System.IAsyncResult?displayProperty=nameWithType> 对象的服务实现。  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>请参阅
- [设计服务协定](../../../docs/framework/wcf/designing-service-contracts.md)
- [同步和异步操作](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
