---
title: 运行时指令元素
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137808"
---
# <a name="runtime-directive-elements"></a>运行时指令元素
运行时指令 (rd.xml) 文件格式支持以下运行时指令元素。 请参阅[运行时指令 (rd.xml) 配置文件参考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)了解分层表示形式。  
  
 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md)  
 将运行时反射策略应用到该应用使用的所有类型，作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。 这是 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 元素的子元素。  
  
 [\<程序集 >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 将运行时策略应用到程序集中的所有类型。 这是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 元素的子元素。  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 如果它包含的 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 指令是一个属性，则将运行时策略应用到应用了该属性的代码元素。  
  
 [\<指令 >](../../../docs/framework/net-native/directives-element-net-native.md)  
 根元素位于 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 的每个运行时指令文件中。 它的子元素是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)。  
  
 [\<事件 >](../../../docs/framework/net-native/event-element-net-native.md)  
 将运行时策略应用到一个事件。 这是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子元素。  
  
 [\<字段 >](../../../docs/framework/net-native/field-element-net-native.md)  
 将运行时策略应用到一个字段。 这是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子元素。  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 将运行时策略应用到一个泛型类型或方法的参数类型。  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 如果该策略已应用到该包含类型或方法，将该运行时策略应用到一个类型。  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 将运行时策略应用到程序集中的所有类型。 这是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 元素的子元素。  
  
 [\<方法 >](../../../docs/framework/net-native/method-element-net-native.md)  
 将运行时策略应用到一个方法。 这是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子元素。  
  
 [\<方法实例化 >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 将运行时策略应用到一个构造泛型方法。 这是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子元素。  
  
 [\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)  
 将运行时策略应用到命名空间中的所有类型。  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 将运行时策略应用到传递到方法的参数类型。  
  
 [\<属性 >](../../../docs/framework/net-native/property-element-net-native.md)  
 将运行时策略应用到一个属性。 这是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 元素的子元素。  
  
 [\<子类型 >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 将运行时策略应用到从包含类型继承的所有类。  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 将运行时策略应用到一个类型。  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 将运行时策略应用到一个构造泛型类型。  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 将运行时策略应用到以传递到方法为代表的 <xref:System.Type> 自变量类型。  
  
## <a name="see-also"></a>请参阅

- [rd.xml 配置文件引用](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
