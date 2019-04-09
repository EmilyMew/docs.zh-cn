---
title: 异常 Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136131"
---
# <a name="exception-thrownv1-etw-event"></a>异常 Thrown_V1 ETW 事件
该事件捕获有关引发的异常的信息。  
  
 下表显示了引发事件的关键字以及事件的级别。 （有关详细信息，请参阅 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)。）  
  
|引发事件的关键字|级别|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|警告 (2)|  
  
 下表显示了事件信息。  
  
|Event|事件 ID|在发生以下情况时引发|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|引发托管异常。|  
  
 下表显示了事件数据。  
  
|字段名|数据类型|描述|  
|----------------|---------------|-----------------|  
|异常类型|win:UnicodeString|异常的类型，例如，`System.NullReferenceException`。|  
|异常消息|win:UnicodeString|实际的异常消息。|  
|EIPCodeThrow|win:Pointer|指向异常发生位置的指令指针。|  
|ExceptionHR|win:UInt32|异常 [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679)。|  
|ExceptionFlags|win:UInt16|0x01:HasInnerException (请参阅[CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)Visual Basic 文档中)。<br /><br /> 0x02:IsNestedException.<br /><br /> 0x04:IsRethrownException。<br /><br /> 0x08:IsCorruptedStateException (表示进程状态已损坏; 请参阅[处理损坏状态异常](https://go.microsoft.com/fwlink/?LinkId=179681)MSDN 上)。<br /><br /> 0x10:IsCLSCompliant (从派生的异常<xref:System.Exception>符合 CLS 規格; 否则为不符合 CLS 規格)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 的实例的唯一 ID。|  
  
## <a name="see-also"></a>请参阅

- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
