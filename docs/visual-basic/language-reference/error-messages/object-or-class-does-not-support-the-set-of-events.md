---
title: 对象或类不支持事件集
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 2e00bdd624b54e19f19b6dabf6681bbf89709e60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822571"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>对象或类不支持事件集
您尝试使用`WithEvents`变量替换为指定的事件集的事件源不能工作的组件。 例如，你想要接收的事件对象，然后创建另一个对象`Implements`的第一个对象。 尽管您可能认为可以实现的对象接收的事件，但这并不总是这种情况。 `Implements` 仅实现的接口方法和属性。 `WithEvents` 不支持私有`UserControls`，因为类型信息所需引发`ObjectEvent`在运行时不可用。  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  不能接收事件不是事件源的组件。  
  
## <a name="see-also"></a>请参阅

- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
- [Implements 语句](../../../visual-basic/language-reference/statements/implements-statement.md)
