---
title: 地址标头
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 133826bbbea62b660bdcdd884ce657528ad30873
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576000"
---
# <a name="address-headers"></a><span data-ttu-id="48954-102">地址标头</span><span class="sxs-lookup"><span data-stu-id="48954-102">Address Headers</span></span>

<span data-ttu-id="48954-103">地址标头示例演示客户端如何使用 Windows Communication Foundation （WCF）将引用参数传递给服务。</span><span class="sxs-lookup"><span data-stu-id="48954-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="48954-104">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="48954-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="48954-105">WS-Addressing 规范将终结点引用的概念定义为对特定 Web 服务终结点寻址的方式。</span><span class="sxs-lookup"><span data-stu-id="48954-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="48954-106">在 WCF 中，使用类对终结点引用进行建模 `EndpointAddress` - `EndpointAddress` 类的地址字段的类型 `ServiceEndpoint` 。</span><span class="sxs-lookup"><span data-stu-id="48954-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="48954-107">作为终结点引用模型的一部分，每个引用都可以携带一些可添加额外标识信息的引用参数。</span><span class="sxs-lookup"><span data-stu-id="48954-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="48954-108">在 WCF 中，这些引用参数建模为类的实例 `AddressHeader` 。</span><span class="sxs-lookup"><span data-stu-id="48954-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="48954-109">在本示例中，客户端将向客户端终结点的 `EndpointAddress` 添加一个引用参数。</span><span class="sxs-lookup"><span data-stu-id="48954-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="48954-110">服务将查找此引用参数并在其“Hello”服务操作的逻辑中使用此参数的值。</span><span class="sxs-lookup"><span data-stu-id="48954-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="48954-111">客户端</span><span class="sxs-lookup"><span data-stu-id="48954-111">Client</span></span>

<span data-ttu-id="48954-112">若要使客户端发送引用参数，该客户端必须向 `AddressHeader` 的 `EndpointAddress` 添加一个 `ServiceEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="48954-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="48954-113">由于 `EndpointAddress` 类是不可变的，因此必须使用 `EndpointAddressBuilder` 类来完成终结点地址的修改。</span><span class="sxs-lookup"><span data-stu-id="48954-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="48954-114">下面的代码将客户端初始化为作为其消息的一部分来发送引用参数。</span><span class="sxs-lookup"><span data-stu-id="48954-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="48954-115">代码使用原始 `EndpointAddressBuilder` 作为初始值创建 `EndpointAddress`。</span><span class="sxs-lookup"><span data-stu-id="48954-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="48954-116">然后添加新创建的地址标头;调用可 `CreateAddressHeader` 创建具有特定名称、命名空间和值的标头。</span><span class="sxs-lookup"><span data-stu-id="48954-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="48954-117">此处值为“John”。</span><span class="sxs-lookup"><span data-stu-id="48954-117">Here the value is "John".</span></span> <span data-ttu-id="48954-118">将标头添加到生成器后，`ToEndpointAddress()` 方法会将生成器（可变）转换回终结点地址（不可变），该地址将分配回给客户端终结点的“地址”字段。</span><span class="sxs-lookup"><span data-stu-id="48954-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="48954-119">现在，当客户端调用 `Console.WriteLine(client.Hello());` 时，服务能够获取此地址参数的值，如客户端生成的输出所示。</span><span class="sxs-lookup"><span data-stu-id="48954-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="48954-120">服务器</span><span class="sxs-lookup"><span data-stu-id="48954-120">Server</span></span>

<span data-ttu-id="48954-121">服务操作 `Hello()` 的实现使用当前 `OperationContext` 来检查传入消息上标头的值。</span><span class="sxs-lookup"><span data-stu-id="48954-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

<span data-ttu-id="48954-122">代码循环访问传入消息上的所有标头，查找具有特定名称并作为引用参数的标头。</span><span class="sxs-lookup"><span data-stu-id="48954-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="48954-123">该找到参数时，代码将读取参数的值并将其保存在“id”变量中。</span><span class="sxs-lookup"><span data-stu-id="48954-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48954-124">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="48954-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="48954-125">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="48954-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="48954-126">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="48954-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="48954-127">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="48954-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48954-128">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="48954-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48954-129">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="48954-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="48954-130">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="48954-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48954-131">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="48954-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
