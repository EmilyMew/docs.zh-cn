---
title: SqlStreamChars.CanSeek 属性 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 52f88a3551e20c74d7a1144c3cd6859a023980db
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633707"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars.CanSeek 属性

当在派生类中重写，获取一个值，该值指示当前流是否支持查找操作。 包含此属性的程序集具有与 SQLAccess.dll 友元关系。 它被用于 SQL server 上。 对于其他数据库，使用提供该数据库的宿主机制。

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>属性值

<xref:System.Boolean>\
`true` 如果当前流支持查找操作;否则为`false`。

## <a name="remarks"></a>备注

> [!WARNING]
> `SqlStreamChars.CanSeek`属性是私有的不适合直接在代码中使用。
>
> Microsoft 不支持在生产应用程序在任何情况下使用此字段。

## <a name="requirements"></a>要求

**Namespace**：<xref:System.Data.SqlTypes>

**程序集：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 之后可用。