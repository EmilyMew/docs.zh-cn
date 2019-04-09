---
title: 如何：创建和绑定到 ObservableCollection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 45f8b097bfdb8d3d7994e53ea05146aa6de0fc21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188430"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>如何：创建和绑定到 ObservableCollection
此示例演示如何创建和绑定到一个集合，其中派生<xref:System.Collections.ObjectModel.ObservableCollection%601>类，该类是一个集合类，添加或移除项时提供通知。  
  
## <a name="example"></a>示例  
 下面的示例演示 `NameList` 集合的实现：  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 可以根据[使数据可用于 XAML 中的绑定](how-to-make-data-available-for-binding-in-xaml.md)中的说明，按照与其他 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 对象相同的方式使集合可用于绑定。 例如，可以在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中实例化该集合，并将该集合指定为一个资源，如下所示：  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 然后可以绑定到该集合：  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 此处没有显示 `NameItemTemplate` 的定义。  
  
> [!NOTE]
>  集合中的对象必须满足[绑定源概述](binding-sources-overview.md)中所述的要求。 具体而言，如果使用的<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>(例如，希望你[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]时更新源属性发生显著变化)，必须实现适当的属性更改通知机制，如<xref:System.ComponentModel.INotifyPropertyChanged>接口。  
  
 有关详细信息，请参阅[数据绑定概述](data-binding-overview.md)中的“绑定到集合”一节。  
  
## <a name="see-also"></a>请参阅

- [在视图中对数据进行排序](how-to-sort-data-in-a-view.md)
- [筛选视图中的数据](how-to-filter-data-in-a-view.md)
- [在 XAML 中使用视图对数据进行排序和分组](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
