---
title: 使用数据协定解析程序
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 20abd4d928fc51eb359949ecbb216615e9659b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595019"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="a80cb-102">使用数据协定解析程序</span><span class="sxs-lookup"><span data-stu-id="a80cb-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="a80cb-103">使用数据协定解析程序可以动态配置已知类型。</span><span class="sxs-lookup"><span data-stu-id="a80cb-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="a80cb-104">序列化或反序列化并非数据协定所需的类型时，要求提供已知类型。</span><span class="sxs-lookup"><span data-stu-id="a80cb-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="a80cb-105">有关已知类型的详细信息，请参阅[数据协定已知类型](data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a80cb-105">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="a80cb-106">已知类型通常以静态方式指定。</span><span class="sxs-lookup"><span data-stu-id="a80cb-106">Known types are normally specified statically.</span></span> <span data-ttu-id="a80cb-107">这意味着您必须了解在实现某个操作期间，该操作可能接收的所有可能类型。</span><span class="sxs-lookup"><span data-stu-id="a80cb-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="a80cb-108">在某些方案中无法做到这一点，因此能够以动态方式指定已知类型十分重要。</span><span class="sxs-lookup"><span data-stu-id="a80cb-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="a80cb-109">创建数据协定解析程序</span><span class="sxs-lookup"><span data-stu-id="a80cb-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="a80cb-110">创建数据协定解析程序涉及到实现两个方法：<xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> 和 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>。</span><span class="sxs-lookup"><span data-stu-id="a80cb-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="a80cb-111">这两个方法分别实现在序列化和反序列化期间使用的回调。</span><span class="sxs-lookup"><span data-stu-id="a80cb-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="a80cb-112">在序列化期间将调用 <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> 方法，用于获取数据协定类型并将其映射到 `xsi:type` 名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="a80cb-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="a80cb-113">在反序列化期间将调用 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> 方法，用于获取 `xsi:type` 名称和命名空间并将其解析为数据协定类型。</span><span class="sxs-lookup"><span data-stu-id="a80cb-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="a80cb-114">这两个方法均具有 `knownTypeResolver` 参数，该参数可用于在实现中使用默认已知类型解析程序。</span><span class="sxs-lookup"><span data-stu-id="a80cb-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="a80cb-115">下面的示例演示了如何实现 <xref:System.Runtime.Serialization.DataContractResolver>，以映射到派生自数据协定类型 `Customer` 的数据协定类型 `Person`，或者从后一个数据协定类型进行映射。</span><span class="sxs-lookup"><span data-stu-id="a80cb-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a80cb-116">一旦定义了 <xref:System.Runtime.Serialization.DataContractResolver>，即可将它传递到 <xref:System.Runtime.Serialization.DataContractSerializer> 构造函数加以使用，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a80cb-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="a80cb-117">可以在对 <xref:System.Runtime.Serialization.DataContractResolver> 或 <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> 方法的调用中指定  <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a80cb-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="a80cb-118">或者，可以在 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 上设置该构造函数，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a80cb-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="a80cb-119">通过实现可以应用于服务的特性，可以通过声明方式指定数据协定解析程序。</span><span class="sxs-lookup"><span data-stu-id="a80cb-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="a80cb-120">有关详细信息，请参阅[KnownAssemblyAttribute](../samples/knownassemblyattribute.md)示例。</span><span class="sxs-lookup"><span data-stu-id="a80cb-120">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="a80cb-121">此示例实现一个名为 "KnownAssembly" 的属性，该属性将自定义数据协定解析程序添加到服务的行为。</span><span class="sxs-lookup"><span data-stu-id="a80cb-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80cb-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a80cb-122">See also</span></span>

- [<span data-ttu-id="a80cb-123">数据协定已知类型</span><span class="sxs-lookup"><span data-stu-id="a80cb-123">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="a80cb-124">DataContractSerializer 示例</span><span class="sxs-lookup"><span data-stu-id="a80cb-124">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="a80cb-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="a80cb-125">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
