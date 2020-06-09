---
title: 对象引用
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ba4ee3fd0cc16130f66570891ecc295b2d2c50aa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599979"
---
# <a name="object-references"></a><span data-ttu-id="f9594-102">对象引用</span><span class="sxs-lookup"><span data-stu-id="f9594-102">Object References</span></span>
<span data-ttu-id="f9594-103">此示例演示如何在服务器与客户端之间通过引用来传递对象。</span><span class="sxs-lookup"><span data-stu-id="f9594-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="f9594-104">该示例使用模拟*社交网络*。</span><span class="sxs-lookup"><span data-stu-id="f9594-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="f9594-105">社会网络由一个 `Person` 类组成，该类包含一个朋友列表，其中每个朋友都是 `Person` 类的一个实例，并有自己的朋友列表。</span><span class="sxs-lookup"><span data-stu-id="f9594-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="f9594-106">这将创建一个对象图。</span><span class="sxs-lookup"><span data-stu-id="f9594-106">This creates a graph of objects.</span></span> <span data-ttu-id="f9594-107">服务在这些社会网络上公开操作。</span><span class="sxs-lookup"><span data-stu-id="f9594-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="f9594-108">在本示例中，服务是由 Internet 信息服务 (IIS) 承载的，客户端是一个控制台应用程序 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="f9594-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9594-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="f9594-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="f9594-110">服务</span><span class="sxs-lookup"><span data-stu-id="f9594-110">Service</span></span>  
 <span data-ttu-id="f9594-111">`Person` 类应用了 <xref:System.Runtime.Serialization.DataContractAttribute> 属性，<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 字段设置为 `true` 以将其声明为引用类型。</span><span class="sxs-lookup"><span data-stu-id="f9594-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="f9594-112">所有属性 (Property) 都应用了 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="f9594-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="f9594-113">`GetPeopleInNetwork` 操作采用一个 `Person` 类型的参数，并返回网络中的所有人；也就是说，返回 `friends` 列表中的所有人、朋友的朋友等等（没有重复项）。</span><span class="sxs-lookup"><span data-stu-id="f9594-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="f9594-114">`GetMutualFriends` 采用一个 `Person` 类型的参数，返回列表中所有符合以下条件的朋友：在其 `friends` 列表中也包含这个人。</span><span class="sxs-lookup"><span data-stu-id="f9594-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="f9594-115">`GetCommonFriends` 操作采用一个 `Person` 类型的列表。</span><span class="sxs-lookup"><span data-stu-id="f9594-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="f9594-116">该列表应当有两个 `Person` 对象。</span><span class="sxs-lookup"><span data-stu-id="f9594-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="f9594-117">该操作返回 `Person` 对象的列表，这些对象位于输入列表中的 `friends` 对象的 `Person` 列表中。</span><span class="sxs-lookup"><span data-stu-id="f9594-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="f9594-118">客户端</span><span class="sxs-lookup"><span data-stu-id="f9594-118">Client</span></span>  
 <span data-ttu-id="f9594-119">使用 Visual Studio 的**添加服务引用**功能创建客户端代理。</span><span class="sxs-lookup"><span data-stu-id="f9594-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="f9594-120">创建了一个由五个 `Person` 对象组成的社会网络。</span><span class="sxs-lookup"><span data-stu-id="f9594-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="f9594-121">客户端在服务中调用三个方法中的每一个。</span><span class="sxs-lookup"><span data-stu-id="f9594-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f9594-122">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f9594-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f9594-123">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f9594-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f9594-124">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f9594-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f9594-125">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f9594-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9594-126">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f9594-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f9594-127">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f9594-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f9594-128">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="f9594-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f9594-129">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f9594-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="f9594-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9594-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="f9594-131">可互操作的对象引用</span><span class="sxs-lookup"><span data-stu-id="f9594-131">Interoperable Object References</span></span>](../feature-details/interoperable-object-references.md)
