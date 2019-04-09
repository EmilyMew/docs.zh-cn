---
title: 本地方法调用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: c8a4c29b1faa3c05f2cf32e9a60104b43a9b1c40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074542"
---
# <a name="local-method-calls"></a>本地方法调用
本地方法调用是在对象模型中执行的方法调用。 远程方法调用是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 转换成 SQL 并传输至数据库引擎进行执行的方法调用。 当 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 无法将调用转换成 SQL 时，将需要本地方法调用。 否则会引发 <xref:System.InvalidOperationException>。  
  
## <a name="example-1"></a>示例 1  
 在下面的示例中，`Order` 类将映射到 Northwind 示例数据库中的 Orders 表。 将一个本地实例方法添加到了此类。  
  
 在查询 1 中，`Order` 类的构造函数是在本地执行的。 在查询 2 中，如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 尝试将 `LocalInstanceMethod()` 转换成 SQL，此尝试将失败并且将引发 <xref:System.InvalidOperationException> 异常。 但由于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 为本地方法调用提供了支持，查询 2 将不会引发异常。  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>请参阅

- [背景信息](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
