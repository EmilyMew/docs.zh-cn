---
title: GUID“<attribute>”的格式不正确，因此无法应用“<number>”
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: ab821db45ae834e82aa134b6f20ded14d43709ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832263"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<属性 > 无法应用，因为 GUID 的格式\<数 > 不正确
一个`COMClassAttribute`特性块指定不符合的正确格式生成 guid 的全局唯一标识符 (GUID)。 `COMClassAttribute` 使用 Guid 来唯一标识类、 接口和创建事件。  
  
 一个 GUID 由 16 个字节组成，其中前八个是数值，而后八个为二进制形式。 它由 Microsoft 的实用工具，例如 uuidgen.exe 生成，保证在空间和时间是唯一的。  
  
 **错误 ID:** BC32500  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  确定正确的 GUID 或 Guid 标识的 COM 对象所需。  
  
2.  确保正确复制提供给 `COMClassAttribute` 特性块的 GUID 字符串。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Guid>
- [属性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)
