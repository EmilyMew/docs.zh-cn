---
title: 终结点：Calls Failed Per Second（每秒失败的调用次数）
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 52419f45adde768d19d6b46642d52ad0a1844197
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100014"
---
# <a name="endpoint-calls-failed-per-second"></a>终结点：Calls Failed Per Second（每秒失败的调用次数）
计数器名称：每秒失败的调用。  
  
## <a name="description"></a>描述  
 一秒钟内通过此终结点收到且具有未处理的异常的调用次数。  
  
 此计数器为性能计数器类型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用以下公式计算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 每当此终结点处有未处理的异常时，此计数器就会增加。  
  
## <a name="see-also"></a>请参阅

- [在协定和服务中指定和处理错误](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
