---
title: Protobuf 消息-WCF 开发人员 gRPC
description: '了解如何在 IDL 中定义 Protobuf 消息，并在 c # 中生成这些消息。'
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325033"
---
# <a name="protobuf-messages"></a><span data-ttu-id="0b33d-103">Protobuf 消息</span><span class="sxs-lookup"><span data-stu-id="0b33d-103">Protobuf messages</span></span>

<span data-ttu-id="0b33d-104">本部分介绍如何在文件中声明协议缓冲区（Protobuf）消息 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="0b33d-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="0b33d-105">它介绍了字段编号和类型的基本概念，并探讨了编译器生成的 c # 代码 `protoc` 。</span><span class="sxs-lookup"><span data-stu-id="0b33d-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="0b33d-106">本章的其余部分将更详细地介绍如何在 Protobuf 中表示不同类型的数据。</span><span class="sxs-lookup"><span data-stu-id="0b33d-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="0b33d-107">声明消息</span><span class="sxs-lookup"><span data-stu-id="0b33d-107">Declaring a message</span></span>

<span data-ttu-id="0b33d-108">在 Windows Communication Foundation （WCF）中，可按 `Stock` 以下示例所示定义股票市场贸易应用程序的类：</span><span class="sxs-lookup"><span data-stu-id="0b33d-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="0b33d-109">若要在 Protobuf 中实现等效类，必须在该文件中声明它 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="0b33d-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="0b33d-110">`protoc`然后，编译器将生成 .net 类作为生成过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="0b33d-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="0b33d-111">第一行声明所使用的语法版本。</span><span class="sxs-lookup"><span data-stu-id="0b33d-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="0b33d-112">语言版本3在2016中发布。</span><span class="sxs-lookup"><span data-stu-id="0b33d-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="0b33d-113">这是我们建议用于 gRPC 服务的版本。</span><span class="sxs-lookup"><span data-stu-id="0b33d-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="0b33d-114">`option csharp_namespace`行指定要用于生成的 c # 类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="0b33d-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="0b33d-115">如果为其他语言编译了文件，则将忽略此选项 `.proto` 。</span><span class="sxs-lookup"><span data-stu-id="0b33d-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="0b33d-116">Protobuf 文件通常包含多种语言的特定于语言的选项。</span><span class="sxs-lookup"><span data-stu-id="0b33d-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="0b33d-117">`Stock`消息定义指定四个字段。</span><span class="sxs-lookup"><span data-stu-id="0b33d-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="0b33d-118">每个都有类型、名称和字段编号。</span><span class="sxs-lookup"><span data-stu-id="0b33d-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="0b33d-119">字段编号</span><span class="sxs-lookup"><span data-stu-id="0b33d-119">Field numbers</span></span>

<span data-ttu-id="0b33d-120">字段编号是 Protobuf 的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="0b33d-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="0b33d-121">它们用于标识二进制编码数据中的字段，这意味着它们不能从版本更改为服务版本。</span><span class="sxs-lookup"><span data-stu-id="0b33d-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="0b33d-122">优点在于可以实现向后兼容性和向前兼容性。</span><span class="sxs-lookup"><span data-stu-id="0b33d-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="0b33d-123">只要处理丢失值的可能性，客户端和服务就会忽略他们不知道的字段编号。</span><span class="sxs-lookup"><span data-stu-id="0b33d-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="0b33d-124">在二进制格式中，字段号与类型标识符组合在一起。</span><span class="sxs-lookup"><span data-stu-id="0b33d-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="0b33d-125">1到15之间的字段编号可以使用其类型编码为单字节。</span><span class="sxs-lookup"><span data-stu-id="0b33d-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="0b33d-126">从16到2047的数字需要2个字节。</span><span class="sxs-lookup"><span data-stu-id="0b33d-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="0b33d-127">如果出于任何原因需要将超过2047个字段，则可以更高。</span><span class="sxs-lookup"><span data-stu-id="0b33d-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="0b33d-128">字段号1到15的单字节标识符提供更好的性能，因此，你应将其用于最基本的常用字段。</span><span class="sxs-lookup"><span data-stu-id="0b33d-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="0b33d-129">类型</span><span class="sxs-lookup"><span data-stu-id="0b33d-129">Types</span></span>

<span data-ttu-id="0b33d-130">类型声明使用 Protobuf 的本机标量数据类型，[下一部分](protobuf-data-types.md)将对此进行更详细的讨论。</span><span class="sxs-lookup"><span data-stu-id="0b33d-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="0b33d-131">本章的其余部分将介绍 Protobuf 的内置类型，并说明它们如何与常见的 .NET 类型相关。</span><span class="sxs-lookup"><span data-stu-id="0b33d-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="0b33d-132">Protobuf 不本机支持 `decimal` 类型，因此 `double` 改用。</span><span class="sxs-lookup"><span data-stu-id="0b33d-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="0b33d-133">对于需要完全小数精度的应用程序，请参阅本章下一部分中[有关小数部分的部分](protobuf-data-types.md#decimals)。</span><span class="sxs-lookup"><span data-stu-id="0b33d-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="0b33d-134">生成的代码</span><span class="sxs-lookup"><span data-stu-id="0b33d-134">The generated code</span></span>

<span data-ttu-id="0b33d-135">构建应用程序时，Protobuf 会为每个消息创建类，并将其本机类型映射到 c # 类型。</span><span class="sxs-lookup"><span data-stu-id="0b33d-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="0b33d-136">生成的 `Stock` 类型将具有以下签名：</span><span class="sxs-lookup"><span data-stu-id="0b33d-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="0b33d-137">生成的实际代码比此要复杂得多。</span><span class="sxs-lookup"><span data-stu-id="0b33d-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="0b33d-138">原因在于，每个类都包含序列化并将自身反序列化为二进制线路格式所需的所有代码。</span><span class="sxs-lookup"><span data-stu-id="0b33d-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="0b33d-139">属性名称</span><span class="sxs-lookup"><span data-stu-id="0b33d-139">Property names</span></span>

<span data-ttu-id="0b33d-140">请注意，Protobuf 编译器应用于 `PascalCase` 属性名称，不过它们 `snake_case` 在 `.proto` 文件中。</span><span class="sxs-lookup"><span data-stu-id="0b33d-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="0b33d-141">[Protobuf 样式指南](https://developers.google.com/protocol-buffers/docs/style)建议 `snake_case` 在消息定义中使用，以便为其他平台生成的代码生成约定所需的大小写。</span><span class="sxs-lookup"><span data-stu-id="0b33d-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0b33d-142">[上一页](protocol-buffers.md)
>[下一页](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="0b33d-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
