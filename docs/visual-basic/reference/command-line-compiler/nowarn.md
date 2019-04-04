---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828207"
---
# <a name="-nowarn"></a>-nowarn
禁止编译器生成警告的能力。  
  
## <a name="syntax"></a>语法  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`numberList`|可选。 应禁止显示编译器警告 ID 号的以逗号分隔列表。 如果未指定警告 Id，则会取消所有警告。|  
  
## <a name="remarks"></a>备注  
 `-nowarn`选项将使编译器不生成警告。 若要禁止显示个别警告，请提供将警告 ID 与`-nowarn`冒号之后的选项。 用逗号分隔多个警告编号。  
  
 需要指定只有警告标识符的数值部分。 例如，如果你想要禁止显示 BC42024，对于未使用的本地变量，警告指定`-nowarn:42024`。  
  
 警告 ID 号的详细信息，请参阅[Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
|在 Visual Studio 集成的开发环境中设置-nowarn|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“编译”选项卡。<br />3.选择**禁用所有警告**复选框以都禁用所有警告。<br />     - 或 -<br />     若要禁用特定警告，请单击**None**警告旁边的下拉列表中。|  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`，不会显示任何警告。  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`，不会显示为未使用的本地变量 (42024) 警告。  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
