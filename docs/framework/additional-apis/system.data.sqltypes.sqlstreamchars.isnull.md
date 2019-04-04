---
title: SqlStreamChars.IsNull 属性 (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ec00b0afa1597c3ae6488c12fe5a0667dad70e2d
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634331"
---
# <a name="sqlstreamcharsisnull-property"></a>SqlStreamChars.IsNull 属性

当在派生类中重写时获取一个值，指示流是否`null`。 包含此属性的程序集具有与 SQLAccess.dll 友元关系。 它被用于 SQL server 上。 对于其他数据库，使用提供该数据库的宿主机制。

## <a name="syntax"></a>语法

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a>属性值

<xref:System.Boolean>\
`true` 如果流已`null`; 否则为`false`。

## <a name="remarks"></a>备注

> [!WARNING]
> `SqlStreamChars.IsNull`属性是私有的不适合直接在代码中使用。
>
> Microsoft 不支持在生产应用程序在任何情况下使用此字段。

## <a name="requirements"></a>要求

**Namespace**：<xref:System.Data.SqlTypes>

**程序集：** System.Data （在 System.Data.dll 中)

**.NET framework 版本：** 自 2.0 之后可用。