---
title: 弱事件模式
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 49795235d489ebc70cec11332e6be4a9452bc21d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139251"
---
# <a name="weak-event-patterns"></a>弱事件模式
在应用程序，很可能附加到事件源的处理程序不会破坏与该处理程序附加到源的侦听器对象结合使用。 这种情况下可能会导致内存泄漏。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 引入了可用于解决此问题，请通过专用管理器类的特定事件并在该事件的侦听器上实现接口的设计模式。 这种设计模式被称为*弱事件模式*。  
  
## <a name="why-implement-the-weak-event-pattern"></a>为什么要实现弱事件模式？  
 侦听事件可能会导致内存泄漏。 为要侦听的事件的典型方法是使用将一个处理程序附加到源中的事件的特定于语言的语法。 例如，在C#，语法是： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。  
  
 此方法创建事件源到事件侦听器的强引用。 通常，为侦听器附加事件处理程序会导致具有受到了源的对象生存期 （除非显式删除事件处理程序） 的对象生存期的侦听器。 但在某些情况下，你可能想要由其他因素控制的侦听器的对象生存期，如是否当前属于可视化树的应用程序，而不是由源的生存期。 只要源对象生存期超出侦听器的对象生存期，正常事件模式会导致内存泄漏： 侦听器保持活动状态比预期更长时间。  
  
 弱事件模式旨在解决此内存泄漏问题。 侦听器需要注册一个事件，但侦听器并不显式了解何时取消注册时，可以使用弱事件模式。 源的对象生存期超过侦听器的有用的对象生存期时，还可以使用弱事件模式。 (在这种情况下，*有用*由您决定。)弱事件模式允许注册和接收事件，而不会影响任何方式侦听器的对象生存期特征的侦听器。 实际上，来自源的隐式的引用不确定侦听器是否处于可进行垃圾回收。 引用是弱引用，因此命名弱事件模式和相关的[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 可以对侦听器进行垃圾回收或销毁，且源可以继续而不保留对现在销毁的对象的非可收集处理程序引用。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>谁应该实现弱事件模式？  
 主要为控件创作者有趣的是实现弱事件模式。 作为控件作者，您有很大程度上责任的行为和包容控件以及对其插入到的应用程序的影响。 这包括控制对象生存期行为，特别是描述的内存泄漏问题的处理。  
  
 某些情况下本质上是有助于使自身在弱事件模式的应用程序。 其中一种方案是数据绑定。 数据绑定中很常见的源对象是完全独立于侦听器对象，它是绑定的目标。 许多方面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]数据绑定已具有弱事件模式应用于事件的实现方式。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>如何实现弱事件模式  
 有三种方法来实现弱事件模式。 下表列出了三种方法，并提供了应何时使用每个的一些指导。  
  
|方法|何时实现|  
|--------------|-----------------------|  
|使用现有的弱事件管理器类|如果你想要订阅的事件具有对应<xref:System.Windows.WeakEventManager>，使用现有的弱事件管理器。 弱事件管理器所包含的 WPF 的列表，请参阅中的继承层次结构<xref:System.Windows.WeakEventManager>类。 由于包含弱事件管理器是有限的可能需要选择其他方法之一。|  
|使用泛型弱事件管理器类|使用通用<xref:System.Windows.WeakEventManager%602>时的现有<xref:System.Windows.WeakEventManager>不可用，您希望轻松地实现，而你并不关心的是效率。 泛型<xref:System.Windows.WeakEventManager%602>效率低于现有或自定义的弱事件管理器。 例如，泛型类执行的更多的反射来发现给定事件的名称的事件。 此外，通过使用泛型注册事件的代码<xref:System.Windows.WeakEventManager%602>是更详细比使用一个现有或自定义<xref:System.Windows.WeakEventManager>。|  
|创建自定义弱事件管理器类|创建自定义<xref:System.Windows.WeakEventManager>时的现有<xref:System.Windows.WeakEventManager>不可用，并且希望获得最佳的效率。 使用自定义<xref:System.Windows.WeakEventManager>来订阅事件将会更高效，但确实会产生编写更多代码开头的成本。|  
|使用第三方弱事件管理器|NuGet 已[几个弱事件管理器](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)和许多 WPF 框架还支持模式 (例如，请参阅[松散耦合的事件订阅的 Prism 的文档](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events))。|

 以下部分介绍如何实现弱事件模式。  出于本文的讨论，以订阅该事件具有以下特征。  
  
-   事件名称是`SomeEvent`。  
  
-   引发事件`EventSource`类。  
  
-   事件处理程序类型： `SomeEventEventHandler` (或`EventHandler<SomeEventEventArgs>`)。  
  
-   该事件传递的类型参数`SomeEventEventArgs`到事件处理程序。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>使用现有的弱事件管理器类  
  
1.  查找现有的弱事件管理器。  
  
     弱事件管理器所包含的 WPF 的列表，请参阅中的继承层次结构<xref:System.Windows.WeakEventManager>类。  
  
2.  使用新的弱事件管理器，而不是普通事件挂钩。  
  
     例如，如果你的代码使用以下模式来订阅事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     将其更改为以下模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同样，如果你的代码使用以下模式来取消订阅事件：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     将其更改为以下模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>使用泛型弱事件管理器类  
  
1.  使用泛型<xref:System.Windows.WeakEventManager%602>类而不是普通事件挂钩。  
  
     当你使用<xref:System.Windows.WeakEventManager%602>若要注册事件侦听器，您提供事件源和<xref:System.EventArgs>类型的类和调用的类型参数作为<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下面的代码中所示：  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>创建自定义的弱事件管理器类  
  
1.  将以下类模板复制到你的项目。  
  
     此类继承<xref:System.Windows.WeakEventManager>类。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  替换为`SomeEventWeakEventManager`名称与你自己的名称。  
  
3.  替换为您的活动的相应名称的前面所述的三个名称。 (`SomeEvent`， `EventSource`，和`SomeEventEventArgs`)  
  
4.  设置为相同的可见性为它所管理的事件的弱事件管理器类的可见性 （公共 / 内部 / 专用）。  
  
5.  使用新的弱事件管理器，而不是普通事件挂钩。  
  
     例如，如果你的代码使用以下模式来订阅事件：  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     将其更改为以下模式：  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同样，如果你的代码使用以下模式来取消订阅某个事件：  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     将其更改为以下模式：  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [路由事件概述](routed-events-overview.md)
- [数据绑定概述](../data/data-binding-overview.md)
