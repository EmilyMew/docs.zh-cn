---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760975"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>试用区域中不允许 IL ret

|   |   |
|---|---|
|详细信息|与 JIT64 实时编译器不同，RyuJIT（在 .NET Framework 4.6 中使用）不允许在试用区域中使用 IL ret 指令。 ECMA-335 规范不允许从试用区域返回，并且没有已知的托管编译器会生成此类 IL。 但是，如果由反射发出生成，则 JIT64 编译器执行此类 IL。|
|建议|如果应用正在生成在试用区域中包含 ret 操作码的 IL，则该应用会面向 .NET Framework 4.5，使用旧的 JIT 并避免此中断。 或者，生成的 IL 可更新为在试用区域之后返回。|
|范围|边缘|
|版本|4.6|
|类型|重定目标|

