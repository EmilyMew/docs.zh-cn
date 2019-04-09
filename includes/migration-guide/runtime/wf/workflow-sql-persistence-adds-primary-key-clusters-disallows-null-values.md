---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760404"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>工作流 SQL 持久性添加主键群集并在某些列中禁止 null 值

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.7 起，SqlWorkflowInstanceStoreSchema.sql 脚本为 SQL 工作流实例存储 (SWIS) 创建的表格使用群集主键。 因此，标识不支持 <code>null</code> 值。 此更改不影响 SWIS 操作。 进行了更新以支持 SQL Server 事务复制。|
|建议|若要体验此更改，SQL 文件 SqlWorkflowInstanceStoreSchemaUpgrade.sql 必须应用到现有安装。 新数据库安装自动具有此更改。|
|范围|边缘|
|Version|4.7|
|类型|运行时|

