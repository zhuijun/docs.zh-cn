---
title: 用于字典的 Protobuf 映射-适用于 WCF 开发人员的 gRPC
description: 了解如何使用 Protobuf 映射来表示 .NET 中的字典类型。
ms.date: 09/09/2019
ms.openlocfilehash: 2c2ae76d47b2309227d22235b5acbe2afa794158
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867460"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="0293f-103">词典的 Protobuf 映射</span><span class="sxs-lookup"><span data-stu-id="0293f-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="0293f-104">可以在消息中表示命名值的任意集合，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="0293f-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="0293f-105">在 .NET 中，这通常通过字典类型来处理。</span><span class="sxs-lookup"><span data-stu-id="0293f-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="0293f-106">协议缓冲区中的 .NET 类型的等效项 <xref:System.Collections.Generic.IDictionary%602> (Protobuf) 为 `map<key_type, value_type>` 类型。</span><span class="sxs-lookup"><span data-stu-id="0293f-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="0293f-107">本部分演示如何 `map` 在 Protobuf 中声明类型，以及如何使用生成的代码。</span><span class="sxs-lookup"><span data-stu-id="0293f-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="0293f-108">在生成的代码中， `map` 字段由类型的只读属性表示 [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] 。</span><span class="sxs-lookup"><span data-stu-id="0293f-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="0293f-109">此类型实现标准 .NET 集合接口，包括 <xref:System.Collections.Generic.IDictionary%602> 。</span><span class="sxs-lookup"><span data-stu-id="0293f-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="0293f-110">映射字段不能直接在消息定义中重复。</span><span class="sxs-lookup"><span data-stu-id="0293f-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="0293f-111">但你可以创建一个包含映射的嵌套消息，并 `repeated` 在消息类型上使用，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0293f-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="0293f-112">在代码中使用 MapField 属性</span><span class="sxs-lookup"><span data-stu-id="0293f-112">Using MapField properties in code</span></span>

<span data-ttu-id="0293f-113">`MapField`从字段生成的 `map` 属性是只读的，并且永远不会是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="0293f-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="0293f-114">若要设置地图属性，请对 `Add(IDictionary<TKey,TValue> values)` 空属性使用方法 `MapField` 以从任何 .net 字典复制值。</span><span class="sxs-lookup"><span data-stu-id="0293f-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="0293f-115">延伸阅读</span><span class="sxs-lookup"><span data-stu-id="0293f-115">Further reading</span></span>

<span data-ttu-id="0293f-116">有关 Protobuf 的详细信息，请参阅官方 [Protobuf 文档](https://developers.google.com/protocol-buffers/docs/overview)。</span><span class="sxs-lookup"><span data-stu-id="0293f-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="0293f-117">[上一页](protobuf-enums.md)
>[下一页](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="0293f-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
