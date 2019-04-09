---
title: DependencyObject 的安全构造函数模式
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: ba8b0a48b2b75a9191553392d5ec0a1f66575807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086723"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObject 的安全构造函数模式
通常，类构造函数不应调用诸如虚拟方法或委托等回叫，其原因是构造函数可作为派生类的构造函数的基本初始化进行调用。 输入该虚拟的操作可能会在任何给定对象的不完全初始化状态下进行。 但是，属性系统本身在内部调用并公开回叫，作为依赖属性系统的一部分。 与设置具有依赖项属性值一样简单操作<xref:System.Windows.DependencyObject.SetValue%2A>调用可能包括回叫某个位置在决定中。 因此，在构造函数体内设置依赖属性值时应保持谨慎（将类型用作基类可能会导致问题）。 没有特定的模式，用于实现<xref:System.Windows.DependencyObject>构造函数可避免对依赖属性状态和内在回叫的特定问题此处进行了说明。  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>属性系统虚拟方法  
 在的计算结果的过程可能会调用以下虚拟方法或回叫<xref:System.Windows.DependencyObject.SetValue%2A>调用，用于设置依赖项属性值： <xref:System.Windows.ValidateValueCallback>， <xref:System.Windows.PropertyChangedCallback>， <xref:System.Windows.CoerceValueCallback>， <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>。 这些虚拟方法或回叫中的每一个在扩展 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 属性系统和依赖属性的多样性方面都具有特定的用途。 有关如何使用这些虚拟方法对属性值确定进行自定义的详细信息，请参阅[依赖属性回调和验证](dependency-property-callbacks-and-validation.md)。  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop 规则强制与属性系统虚拟方法  
 如果将 Microsoft 工具 FXCop 用作生成过程的一部分，并从某些调用基构造函数的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 框架类派生，或在派生的类上实现自己的依赖属性，则可能会违反某个 FXCop 规则。 此违反事件的名称字符串为：  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 此规则是为 FXCop 设置的默认公共规则的一部分。 此规则所报告的内容可能为通过依赖属性系统实现的跟踪情况，该系统会最终调用依赖属性系统虚拟方法。 即使遵循本主题中介绍并建议使用的构造函数模式，仍可能存在此规则冲突，因此可能需要在 FXCop 规则设置配置中禁用或取消该规则。  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>大多数问题是因派生类导致的，而不是因为使用现有类所致  
 当按构造顺序使用虚拟方法实现一个类后从该类进行派生时，便会发生此规则所报告的问题。 如果密封了类，或者确信不会派生自此类或强制不得派生自此类，则此处介绍的注意事项和触发 FXCop 规则的问题将不适用。 但是，如果出于将类用作基类的目的来创作类，例如，如果正创建模板或可扩展的控件库集，则应遵循此处建议的用于构造函数的模式。  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>默认构造函数必须初始化由回叫请求的所有值  
 由类重写或回叫（来自“属性系统虚拟方法”部分列表中的回叫）使用的任何实例成员必须在类的默认构造函数中进行初始化，即使其中的某些值通过非默认构造函数的参数填充为“真实”值时也是如此。  
  
 以下代码示例（和后面的示例）是一个与此规则冲突的伪 C# 示例，其中对问题进行了说明：  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 当应用程序代码调用 `new MyClass(objectvalue)` 时，这会调用默认构造函数和基类构造函数。 然后它会设置`Property1 = object1`，它调用虚拟方法`OnPropertyChanged`上的拥有`MyClass` <xref:System.Windows.DependencyObject>。  重写引用尚未初始化的 `_myList`。  
  
 避免这些问题的一个方法是：确保回叫仅使用其他依赖属性，并且每个这样的依赖属性都有一个确立的默认值作为其注册元数据的一部分。  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>安全构造函数模式  
 若要在将类用作基类的情况下规避未完全实现初始化的风险，请遵循以下模式：  
  
#### <a name="default-constructors-calling-base-initialization"></a>用于调用基本初始化的默认构造函数  
 实现以下用于调用基本默认值的构造函数：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>非默认（方便）构造函数，不与任何基本签名匹配  
 如果这些构造函数使用参数来设置初始化中的依赖属性，首先应调用自己的类默认构造函数进行初始化，然后使用参数来设置依赖属性。 这些可能是类所定义的依赖属性，也可能是从基类继承的依赖属性，但在这两种情况下都使用以下模式：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>非默认（方便）构造函数，确实与基本签名匹配  
 不调用具有相同参数设置的基构造函数，而是再次调用自己的类的默认构造函数。 请勿调用基本初始值设定项，而应调用 `this()`。 然后使用传递的参数作为用于设置相关属性的值来重现原始构造函数行为。 将原始基本构造函数文档用作指导依据，确定要对特定参数设置的属性：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>必须匹配所有签名  
 对于基类型具有多个签名的情况，必须在设置更多属性之前特意将所有可能的签名与自己的构造函数的实现相匹配，该实现使用建议的类默认构造函数调用模式。  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>使用 SetValue 设置依赖属性  
 如果您在设置一个属性，没有为属性设置方便起见，包装，并且设置的值，这些模式同样适用<xref:System.Windows.DependencyObject.SetValue%2A>。 对调用<xref:System.Windows.DependencyObject.SetValue%2A>通过构造函数参数阶段还应调用类的默认构造函数进行初始化。  
  
## <a name="see-also"></a>请参阅

- [自定义依赖项属性](custom-dependency-properties.md)
- [依赖项属性概述](dependency-properties-overview.md)
- [依赖项属性的安全性](dependency-property-security.md)
