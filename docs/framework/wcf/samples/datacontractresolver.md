---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: c2a2afaa450e9abe17b62f6be07a2dc41459ca20
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600018"
---
# <a name="datacontractresolver"></a><span data-ttu-id="6a7ef-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="6a7ef-102">DataContractResolver</span></span>
<span data-ttu-id="6a7ef-103">此示例演示如何使用 <xref:System.Runtime.Serialization.DataContractResolver> 类来自定义序列化和反序列化过程。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="6a7ef-104">此示例演示在序列化和反序列化过程中，如何使用 DataContractResolver 在 CLR 类型与 xsi:type 表示形式之间进行映射。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="6a7ef-105">示例详细信息</span><span class="sxs-lookup"><span data-stu-id="6a7ef-105">Sample Details</span></span>
 <span data-ttu-id="6a7ef-106">此示例定义以下 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="6a7ef-107">此示例加载程序集，提取每个类型，然后对这些类型进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="6a7ef-108"><xref:System.Runtime.Serialization.DataContractResolver> 会通过将 <xref:System.Runtime.Serialization.DataContractResolver> 派生类的实例传递给 <xref:System.Runtime.Serialization.DataContractSerializer> 构造函数，插入到序列化过程中，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="6a7ef-109">此示例随后序列化 CLR 类型，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="6a7ef-110">此示例随后反序列化 xsi:type，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="6a7ef-111">由于会将自定义 <xref:System.Runtime.Serialization.DataContractResolver> 传入到 <xref:System.Runtime.Serialization.DataContractSerializer> 构造函数中，因此在序列化过程中会调用 <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>，以将 CLR 类型映射到等效的 `xsi:type`。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="6a7ef-112">同样，会在反序列化过程中调用 <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>，以将 `xsi:type` 映射到等效的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="6a7ef-113">在此示例中定义了 <xref:System.Runtime.Serialization.DataContractResolver>，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="6a7ef-114">下面的代码示例是一个派生自 <xref:System.Runtime.Serialization.DataContractResolver> 的类。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="6a7ef-115">作为此示例的一部分，Types 项目将生成具有此示例中所使用的全部类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="6a7ef-116">使用此项目可添加、移除或修改将要序列化的所有类型。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6a7ef-117">使用此示例</span><span class="sxs-lookup"><span data-stu-id="6a7ef-117">To use this sample</span></span>

1. <span data-ttu-id="6a7ef-118">使用 Visual Studio 2012 打开 DCRSample 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="6a7ef-119">若要运行解决方案，请按 F5。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a7ef-120">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a7ef-121">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="6a7ef-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6a7ef-122">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="6a7ef-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a7ef-123">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="6a7ef-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="6a7ef-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a7ef-124">See also</span></span>

- [<span data-ttu-id="6a7ef-125">使用数据协定解析程序</span><span class="sxs-lookup"><span data-stu-id="6a7ef-125">Using a Data Contract Resolver</span></span>](../feature-details/using-a-data-contract-resolver.md)
