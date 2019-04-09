---
title: Calls Failed Per Second（每秒失败的调用次数）
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178615"
---
# <a name="calls-failed-per-second"></a>Calls Failed Per Second（每秒失败的调用次数）
计数器名称：Calls Failed Per Second（每秒失败的调用次数）  
  
## <a name="description"></a>描述  
 该操作中每秒钟出现未处理异常的调用数目。  
  
 此计数器为性能计数器类型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用以下公式计算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 该操作中每出现一个未处理的异常，此计数器就会增加。  
  
## <a name="see-also"></a>请参阅

- [在协定和服务中指定和处理错误](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
