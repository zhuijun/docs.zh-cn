---
title: 如何：使用 DataContractJsonSerializer
description: 了解如何将 .NET 类型对象序列化为 JSON 编码数据，然后将此类数据反序列化为 .NET 类型的实例。
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246800"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="f1334-103">如何使用 DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="f1334-103">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="f1334-104">本文介绍 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f1334-104">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="f1334-105">对于涉及序列化和反序列化 JSON 的大多数方案，我们建议在[System.Text.Js上命名空间](../../../standard/serialization/system-text-json-overview.md)中的 api。</span><span class="sxs-lookup"><span data-stu-id="f1334-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="f1334-106">JSON（JavaScript 对象符号）是一种高效的数据编码格式，可用于在客户端浏览器和支持 AJAX 的 Web 服务之间快速交换少量数据。</span><span class="sxs-lookup"><span data-stu-id="f1334-106">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="f1334-107">本文演示如何将 .NET 类型对象序列化为 JSON 编码数据，然后将 JSON 格式的数据反序列化为 .NET 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="f1334-107">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="f1334-108">此示例使用数据协定演示用户定义类型的序列化和反序列化 `Person` ，并使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f1334-108">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="f1334-109">通常，当你在服务操作中使用在支持 AJAX 的终结点上公开的数据协定类型时，将 Windows Communication Foundation 自动处理 JSON 序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="f1334-109">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="f1334-110">但是，在某些情况下，您可能需要直接处理 JSON 数据。</span><span class="sxs-lookup"><span data-stu-id="f1334-110">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="f1334-111">本文基于[DataContractJsonSerializer 示例](../samples/json-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="f1334-111">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="f1334-112">为 Person 类型定义数据协定</span><span class="sxs-lookup"><span data-stu-id="f1334-112">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="f1334-113">通过将 `Person` 附加到类并将 <xref:System.Runtime.Serialization.DataContractAttribute> 特性附加到要序列化的成员，为 <xref:System.Runtime.Serialization.DataMemberAttribute> 定义数据协定。</span><span class="sxs-lookup"><span data-stu-id="f1334-113">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="f1334-114">有关数据协定的详细信息，请参阅[设计服务协定](../designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="f1334-114">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

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

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="f1334-115">将 Person 类型的实例序列化为 JSON</span><span class="sxs-lookup"><span data-stu-id="f1334-115">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="f1334-116">如果在服务器上的传出答复序列化过程中出现错误，或出于其他原因导致错误，则可能不会将其作为错误返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="f1334-116">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="f1334-117">创建 `Person` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="f1334-117">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="f1334-118">`Person`使用将对象序列化到内存流 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f1334-118">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="f1334-119">使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 方法将 JSON 数据写入到流中。</span><span class="sxs-lookup"><span data-stu-id="f1334-119">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="f1334-120">显示 JSON 输出。</span><span class="sxs-lookup"><span data-stu-id="f1334-120">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="f1334-121">从 JSON 反序列化 Person 类型的实例</span><span class="sxs-lookup"><span data-stu-id="f1334-121">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="f1334-122">通过使用 `Person` 的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> 方法，将 JSON 编码数据反序列化为一个新的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 实例。</span><span class="sxs-lookup"><span data-stu-id="f1334-122">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="f1334-123">显示结果。</span><span class="sxs-lookup"><span data-stu-id="f1334-123">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="f1334-124">示例</span><span class="sxs-lookup"><span data-stu-id="f1334-124">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="f1334-125">对于包含多个具有相同名称的成员的数据协定，JSON 序列化程序将引发一个序列化异常，如以下示例代码中所示。</span><span class="sxs-lookup"><span data-stu-id="f1334-125">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f1334-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="f1334-126">See also</span></span>

- [<span data-ttu-id="f1334-127">.NET 中的 JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="f1334-127">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
