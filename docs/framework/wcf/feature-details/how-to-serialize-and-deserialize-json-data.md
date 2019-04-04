---
title: 如何：序列化和反序列化 JSON 数据
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: c5da34b6ab7953dbff62ca757ba08d0c7364b4cf
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465199"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>如何：序列化和反序列化 JSON 数据
JSON（JavaScript 对象符号）是一种高效的数据编码格式，可用于在客户端浏览器和支持 AJAX 的 Web 服务之间快速交换少量数据。  
  
 本文演示如何以.NET 类型对象序列化为 JSON 编码数据，然后以 JSON 格式的数据反序列化回.NET 类型的实例。 此示例使用数据协定演示序列化和反序列化的用户定义`Person`类型，并使用<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。  
  
 通常情况下，JSON 序列化和反序列化自动处理由 Windows Communication Foundation (WCF) 通过启用 AJAX 的终结点公开的服务操作中使用数据协定类型时。 但是，在某些情况下，您可能需要直接处理 JSON 数据。   
  
> [!NOTE]
>  如果在服务器上或某些其他原因的传出答复的序列化期间发生错误，它可能不获取返回到客户端作为错误。  
  
 这篇文章基于[JSON 序列化](../samples/json-serialization.md)示例。  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>若要定义一个 Person 类型的数据协定 
  
1.  通过将 `Person` 附加到类并将 <xref:System.Runtime.Serialization.DataContractAttribute> 特性附加到要序列化的成员，为 <xref:System.Runtime.Serialization.DataMemberAttribute> 定义数据协定。 有关数据协定的详细信息，请参阅[设计服务协定](../designing-service-contracts.md)。  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>将 Person 类型的实例序列化为 JSON  
  
1.  创建 `Person` 类型的实例。  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  序列化`Person`到使用内存流<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法将 JSON 数据写入到流中。  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  显示 JSON 输出。  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>从 JSON 反序列化 Person 类型的实例  
  
1.  通过使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，将 JSON 编码数据反序列化为一个新的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 实例。  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  显示结果。  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>示例  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  对于包含多个具有相同名称的成员的数据协定，JSON 序列化程序将引发一个序列化异常，如以下示例代码中所示。  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>请参阅
- [独立 JSON 序列化](stand-alone-json-serialization.md)
- [支持 JSON 和其他数据传输格式](support-for-json-and-other-data-transfer-formats.md)
